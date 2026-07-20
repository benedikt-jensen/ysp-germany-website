<template>
    <div class="py-6 px-6 mx-0 mt-20 lg:mx-20">
        <div class="grid grid-cols-12 gap-4">
            <div class="col-span-12 md:col-span-2">
                <a class="flex flex-wrap items-center justify-center md:justify-start md:mb-0 mb-4 cursor-pointer">
                    <YspLogo fill-color="var(--p-primary-color)" style="width:80px;height:80px;"/>
                </a>
            </div>

            <div class="col-span-12 md:col-span-10">
                <div class="grid grid-cols-12 gap-8 text-center md:text-left">

                    <div class="col-span-12 md:col-span-3">
                        <h4 class="font-medium text-2xl leading-normal mb-4 text-surface-900 dark:text-surface-0">Community</h4>
                        <a class="leading-normal text-xl block cursor-pointer mb-2 text-surface-700 dark:text-surface-100" href="https://www.instagram.com/ysp.germany/" target="_blank">Instagram</a>
                    </div>

                    <div class="col-span-12 md:col-span-3">
                        <h4 class="font-medium text-2xl leading-normal mb-4 text-surface-900 dark:text-surface-0">Verein</h4>
                        <a class="leading-normal text-xl block cursor-pointer mb-2 text-surface-700 dark:text-surface-100" @click="showSatzung = true">Satzung</a>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <Dialog v-model:visible="showSatzung" modal header="Satzung" :style="{ width: '52rem' }" :breakpoints="{ '960px': '75vw', '640px': '90vw' }">
        <div class="max-h-[70vh] overflow-y-auto pr-2">
            <p class="text-center font-semibold text-xl mb-1 text-surface-900 dark:text-surface-0">Youth and Students for Peace (YSP) Deutschland</p>
            <p class="text-center text-surface-500 dark:text-surface-300 mb-6">Satzung</p>

            <div v-for="section in satzungSections" :key="section.number" class="mb-6">
                <h3 class="font-semibold text-lg mb-2 text-surface-900 dark:text-surface-0">§ {{ section.number }} {{ section.title }}</h3>
                <p v-for="(paragraph, i) in section.paragraphs" :key="i" class="mb-2 text-surface-700 dark:text-surface-100 leading-relaxed">{{ paragraph }}</p>
                <ul v-if="section.list" class="list-disc pl-6 mb-2 text-surface-700 dark:text-surface-100 leading-relaxed">
                    <li v-for="(item, i) in section.list" :key="i">{{ item }}</li>
                </ul>
                <p v-if="section.closing" class="text-surface-700 dark:text-surface-100 leading-relaxed">{{ section.closing }}</p>
            </div>
        </div>
    </Dialog>
</template>
<script setup lang="ts">
import YspLogo from "@/components/ysp/YspLogo.vue";
import { ref } from "vue";

const showSatzung = ref(false);

const satzungSections = [
    {
        number: "1",
        title: "Name und Sitz",
        paragraphs: [
            "Der Name des Vereins lautet: Youth and Students for Peace Deutschland.",
            "Die Abkürzung von Youth and Students for Peace ist YSP.",
            "Der Verein soll in das Vereinsregister eingetragen werden und trägt dann den Zusatz „e.V.“",
            "Der Sitz des Vereins ist Gießen an der Lahn.",
            "Der Verein wurde am 26.01.2019 gegründet."
        ]
    },
    {
        number: "2",
        title: "Zweck",
        paragraphs: [
            "Der Verein verfolgt ausschließlich und unmittelbar gemeinnützige Zwecke im Sinne des Abschnitts „Steuerbegünstigte Zwecke“ der Abgabenordnung.",
            "Zwecke im Einzelnen:"
        ],
        list: [
            "Ausbau eines globalen Friedens-Netzwerks junger Menschen über nationale, kulturelle und religiöse Grenzen hinweg durch interkulturelle und interreligiöse Friedensprojekte und Events.",
            "Stärkung von Individuen und Familien durch Charakterbildung und respektvolle Kommunikation, um friedliche zwischenmenschliche Beziehungen zu fördern.",
            "Förderung eines gesunden und umweltfreundlichen Lebensstils, um die Umwelt nachhaltig zu schonen.",
            "Förderung internationaler Austauschprogramme für junge Menschen, um internationale Freundschaften zu fördern.",
            "Förderung verantwortungsvoller Führung durch Zusammenarbeit mit den Vereinten Nationen, nationalen und regionalen Regierungen sowie gemeinnützigen und religiösen Organisationen. Dabei sollen u.a. die Ziele für nachhaltige Entwicklung der Vereinten Nationen gefördert werden."
        ],
        closing: "Um diese Zwecke zu verwirklichen, wird der Verein durch Publikationen, Workshops, Diskussionen, Vorträge, Filmvorführungen, Seminare, Lehrgänge, internationalen Austausch, Hilfsprojekte und andere geeignete Mittel tätig. YSP behält sich vor, andere Aktivitäten gleicher Zielsetzung zu fördern und zu unterstützen."
    },
    {
        number: "3",
        title: "Mittel und Mittelverwendung",
        paragraphs: [
            "Der Verein ist uneigennützig tätig; er verfolgt keinen eigenwirtschaftlichen Zweck.",
            "Die Mittel zur Erfüllung seiner Aufgaben bestreitet der Verein aus Spenden und Mitgliedsbeiträgen. Über die Festsetzung und die Höhe des Mitgliedsbeitrages beschließt die Mitgliederversammlung.",
            "Mittel des Vereins dürfen nur für die satzungsmäßigen Zwecke verwendet werden. Die Mitglieder erhalten keine Gewinnanteile und in ihrer Eigenschaft als Mitglieder auch keine sonstigen Zuwendungen aus Mitteln des Vereins. Es darf keine Person durch Ausgaben, die dem Zweck des Vereins fremd sind, oder durch unverhältnismäßig hohe Vergütungen begünstigt werden.",
            "Bei Bedarf können Vereinsämter im Rahmen der haushaltsrechtlichen Möglichkeiten entgeltlich auf der Grundlage eines Dienstvertrages oder gegen Zahlung einer Aufwandsentschädigung nach § 3 Nr. 26a EStG ausgeübt werden. Die Entscheidung über eine entgeltliche Vereinstätigkeit trifft der Vorstand. Gleiches gilt für die Vertragsinhalte und die Vertragsbeendigung."
        ]
    },
    {
        number: "4",
        title: "Mitgliedschaft",
        paragraphs: [
            "Mitglied kann jede natürliche Person werden, die mit den satzungsgemäßen Zielen von YSP Deutschland e.V. übereinstimmt.",
            "Über den schriftlichen Aufnahmeantrag entscheidet der Vorstand.",
            "Nur Mitglieder haben in der Mitgliederversammlung von YSP Deutschland e.V. das aktive und passive Wahlrecht.",
            "Der Mitgliedsbeitrag beträgt 40 € pro Jahr für ordentliche Mitglieder und 20 € pro Jahr für Mitglieder mit Ermäßigung (Studenten, Azubis, Schüler und Geringverdiener).",
            "Die Dauer der Mitgliedschaft steht jedem Mitglied frei. Der Austritt wird wirksam mit schriftlicher Mitteilung an den Vorstand.",
            "Die Mitgliedschaft erlischt automatisch mit dem Tode eines Mitglieds.",
            "Ein Mitglied kann vom Verein ausgeschlossen werden, wenn es sich gegen die Interessen des Vereins verhält. Über den Ausschluss entscheidet der Vorstand. Der Ausschluss wird wirksam mit schriftlicher Mitteilung an das Mitglied durch einfachen Brief an die zuletzt bekannte Anschrift des Mitgliedes. Dem ausgeschlossenen Mitglied steht es frei, gegen den Ausschluss vor der Mitgliederversammlung Einspruch zu erheben. Über den Einspruch entscheidet die Mitgliederversammlung mit einfacher Mehrheit."
        ]
    },
    {
        number: "5",
        title: "Ortsgruppen",
        paragraphs: [
            "Den Mitgliedern von YSP Deutschland e.V. steht es frei, sich innerhalb Deutschlands lokal selbst zu organisieren.",
            "Geschäftsordnung und tatsächliche Geschäftsführung von Ortsgruppen dürfen der Satzung von YSP Deutschland e.V. nicht widersprechen.",
            "Die Ortsgruppen dürfen den Namen YSP mit dem Zusatz des Namens ihrer jeweiligen Stadt erst dann offiziell führen, wenn ihre Geschäftsordnung und ihre Verantwortlichen vom Vorstand von YSP Deutschland e.V. schriftlich bestätigt worden sind.",
            "Verantwortliche einer Ortsgruppe gelten als besondere Vertreter des Vereins im Sinne des § 30 BGB. Ihre Vertretungsmacht erstreckt sich auf alle Geschäfte, die die Ortsgruppe zur Erfüllung des Vereinszweckes benötigt. Im Innenverhältnis haften sie jedoch für alle Geschäfte, für die sie keine ausdrückliche Bevollmächtigung erhalten haben.",
            "Die Verantwortlichen von Ortsgruppen sind dem Vorstand der YSP Deutschland e.V. rechenschaftspflichtig. Sie haben umgehend"
        ],
        list: [
            "über Publikationen im Vorhinein zu informieren,",
            "neue Mitglieder zu melden,",
            "alle Ausgaben im Vorhinein genehmigen zu lassen und nach Abschluss der Aktion abzurechnen."
        ]
    },
    {
        number: "6",
        title: "Vorstand",
        paragraphs: ["Der Vorstand setzt sich wie folgt zusammen:"],
        list: [
            "1. Vorsitzender",
            "Stellvertretender Vorsitzender",
            "Schatzmeister",
            "Schriftführer",
            "Drei Beisitzer"
        ],
        closing: "Der Vorstand des Vereins wird von der Mitgliederversammlung für die Dauer von zwei Jahren gewählt. Er führt die Geschäfte bis zu einer Neuwahl fort. Die Bestellung ist nur bei Vorliegen eines wichtigen Grundes widerruflich. Für den Fall, dass ein Vorstandsmitglied während seiner Amtsperiode ausscheidet, wird über die Neubesetzung für die restliche Amtsperiode durch den Vorstand entschieden. Die Beschlüsse des Vorstands werden mit einfacher Mehrheit gefasst. Bei Stimmengleichheit entscheidet die Stimme des 1. Vorsitzenden. Der Verein wird durch zwei Vorstandsmitglieder, von denen einer der 1. Vorsitzende oder der stellvertretender Vorsitzender sein muss, vertreten. Die Vorstandsmitglieder sind von den Beschränkungen des § 181 BGB befreit."
    },
    {
        number: "7",
        title: "Mitgliederversammlung",
        paragraphs: [
            "Mindestens einmal alle zwei Jahre hat der 1. Vorsitzende unter Bekanntgabe der Tagesordnung die Mitgliederversammlung einzuberufen – zur Vorlage des Jahresberichts des Vorstands und zur Entscheidung über alle anderen Fragen, die der Entscheidung der Mitgliederversammlung unterliegen.",
            "Die Einberufung der Mitgliederversammlung erfolgt schriftlich und zwar mindestens zwei Wochen vor dem Versammlungstermin.",
            "Alle Beschlüsse der Mitgliederversammlung werden mit einfacher Mehrheit gefasst, jedoch bedarf eine Änderung der Satzung sowie die Auflösung des Vereins der Zustimmung von Dreiviertel der anwesenden stimmberechtigten Mitglieder.",
            "Die Mitgliederversammlung muss einberufen werden, wenn mindestens 10 Mitglieder unter Angabe eines wichtigen Grundes es verlangen.",
            "Das Protokoll über die Beschlüsse der Mitgliederversammlung wird von einem Schriftführer geführt, der von der Mitgliederversammlung bestimmt wird. Es ist vom 1. Vorsitzenden und einem weiteren Vorstandsmitglied und dem Schriftführer zu unterzeichnen."
        ]
    },
    {
        number: "8",
        title: "Auflösung des Vereins",
        paragraphs: [
            "Die Auflösung des Vereins kann nur in einer Mitgliederversammlung mit der im § 7 festgelegten Stimmenmehrheit beschlossen werden. Sofern die Mitgliederversammlung nichts anderes beschließt, sind der 1. Vorsitzende und ein Stellvertretender Vorsitzender gemeinsam vertretungsberechtigte Liquidatoren.",
            "Bei Auflösung des Vereins oder bei Wegfall des bisherigen Zwecks fällt das Vermögen des Vereins an eine andere steuerbegünstigte Körperschaft zwecks Verwendung zur Unterstützung von Projekten, die ähnliche Ziele wie YSP verfolgen, zu. Diese Körperschaft wird vom Vorstand ausgewählt."
        ]
    }
];
</script>
