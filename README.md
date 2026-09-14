<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Immobilien-Quiz | Gesprächsvorbereitung</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <main class="app">
        <section id="startScreen" class="start">
            <div class="welcome-heart" aria-hidden="true">❤️</div>
            <h1 class="welcome-title">Hallo Melisa</h1>
            <p class="welcome-text">Viel Spaß beim Lernen ❤️</p>
            <p class="sub">85 Fragen für dein Gespräch bei Engel & Völkers</p>
            <ul>
                <li>Start mit leichten Fragen</li>
                <li>Nach 6 richtigen Antworten in Folge steigt die Schwierigkeit</li>
                <li>Bei einer falschen Antwort oder Zeitüberschreitung beginnt die Serie erneut</li>
                <li>20 Sekunden Zeit pro Frage und Zeitbonus</li>
                <li>3 Leben und Erklärung nach jeder Antwort</li>
                <li>Highscore wird im Browser gespeichert</li>
            </ul>
            <button class="control-button" id="startButton">Quiz starten</button>
            <small class="legal-note">Die rechtlichen, steuerlichen und finanziellen Fragen dienen ausschließlich der Gesprächsvorbereitung und ersetzen keine fachliche Beratung.</small>
        </section>

        <section id="game" hidden>
            <h1>Immobilien-Quiz</h1>
            <p class="sub">Fachwissen, Vertrieb, Kaltakquise und Einwandbehandlung</p>
            
            <div class="stats">
                <div class="stat">
                    <small>Frage</small>
                    <span id="position">1/85</span>
                </div>
                <div class="stat">
                    <small>Schwierigkeit</small>
                    <span id="level">Leicht</span>
                </div>
                <div class="stat">
                    <small>Punkte</small>
                    <span id="score">0</span>
                </div>
                <div class="stat">
                    <small>Leben</small>
                    <span id="lives">❤️❤️❤️</span>
                </div>
                <div class="stat">
                    <small>Highscore</small>
                    <span id="highscore">0</span>
                </div>
            </div>

            <div class="bar">
                <div id="progress"></div>
            </div>

            <div id="timer">Zeit: 20 Sekunden</div>
            <h2 id="question"></h2>
            <div id="meta"></div>
            <div id="answers" role="list"></div>
            <div id="feedback" aria-live="polite" role="status">Wähle eine Antwort.</div>

            <div class="controls">
                <button class="control-button" id="nextButton">Nächste Frage</button>
                <button class="control-button" id="restartButton">Neu starten</button>
            </div>
        </section>
    </main>

    <script src="js/questions.js"></script>
    <script src="js/app.js"></script>
</body>
</html>
:root {
    --bg: #101827;
    --panel: #1e293b;
    --soft: #334155;
    --text: #f8fafc;
    --muted: #cbd5e1;
    --gold: #d5b574;
    --green: #22c55e;
    --red: #ef4444;
    --blue: #38bdf8;
    --pink: #f4a6bd;
}

* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    padding: 22px;
    display: grid;
    place-items: center;
    font-family: Arial, Helvetica, sans-serif;
    color: var(--text);
    background: linear-gradient(135deg, #0f172a, #1e293b);
}

.app {
    width: min(900px, 100%);
    padding: 26px;
    background: rgba(30, 41, 59, 0.97);
    border: 1px solid #475569;
    border-radius: 22px;
    box-shadow: 0 24px 60px rgba(0, 0, 0, 0.45);
}

h1 {
    margin: 0;
    color: var(--gold);
    font-size: clamp(26px, 5vw, 42px);
}

.sub {
    margin: 7px 0 20px;
    color: var(--muted);
}

.start {
    padding: 25px 4px;
    text-align: center;
}

.start ul {
    max-width: 620px;
    margin: 22px auto;
    color: var(--muted);
    line-height: 1.7;
    text-align: left;
}

.welcome-heart {
    display: inline-block;
    margin-bottom: 16px;
    font-size: clamp(72px, 16vw, 120px);
    line-height: 1;
    animation: pulse 1.4s ease-in-out infinite;
    filter: drop-shadow(0 8px 18px rgba(239, 68, 68, 0.35));
}

.welcome-title {
    color: var(--pink);
}

.welcome-text {
    font-size: clamp(20px, 4vw, 28px);
    font-weight: 700;
}

@keyframes pulse {
    50% {
        transform: scale(1.12);
    }
}

.stats {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 9px;
    margin: 15px 0;
}

.stat {
    padding: 11px;
    background: #0f172a;
    border-radius: 12px;
    text-align: center;
    font-weight: 700;
}

.stat small {
    display: block;
    margin-bottom: 4px;
    color: var(--muted);
    font-weight: 400;
}

.bar {
    height: 9px;
    margin: 14px 0 22px;
    overflow: hidden;
    background: #0f172a;
    border-radius: 20px;
}

#progress {
    width: 0;
    height: 100%;
    background: linear-gradient(90deg, var(--gold), #f8d899);
    transition: width 0.3s;
}

#timer {
    font-size: 18px;
    font-weight: 700;
}

.timer-warning {
    color: #fbbf24;
}

#question {
    margin: 16px 0 20px;
    font-size: clamp(20px, 3vw, 28px);
    line-height: 1.35;
}

#meta {
    color: var(--muted);
    font-size: 14px;
}

#answers {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
}

.answer {
    padding: 15px;
    color: #fff;
    background: var(--soft);
    border: 1px solid #64748b;
    border-radius: 13px;
    font-size: 16px;
    text-align: left;
    cursor: pointer;
    transition: 0.15s;
}

.answer:hover:not(:disabled) {
    border-color: var(--gold);
    transform: translateY(-2px);
}

.answer.correct {
    background: #166534;
    border-color: var(--green);
}

.answer.wrong {
    background: #991b1b;
    border-color: var(--red);
}

.answer:disabled {
    cursor: default;
    opacity: 0.9;
}

.answer:focus {
    outline: 3px solid rgba(213, 181, 116, 0.6);
}

#feedback {
    min-height: 72px;
    margin-top: 18px;
    padding: 13px;
    background: #0f172a;
    border-radius: 12px;
    line-height: 1.45;
}

.controls {
    display: flex;
    justify-content: flex-end;
    gap: 10px;
    margin-top: 15px;
}

.control-button {
    padding: 12px 18px;
    border: 0;
    border-radius: 11px;
    font-weight: 700;
    cursor: pointer;
}

#startButton,
#nextButton {
    color: #111827;
    background: var(--gold);
    font-size: 18px;
}

#nextButton,
#restartButton {
    display: none;
}

#restartButton {
    color: #082f49;
    background: var(--blue);
}

.legal-note {
    display: block;
    margin-top: 18px;
    color: var(--muted);
    font-size: 13px;
    line-height: 1.5;
}

@media (max-width: 650px) {
    .app {
        padding: 18px;
    }

    .stats {
        grid-template-columns: repeat(2, 1fr);
    }

    #answers {
        grid-template-columns: 1fr;
    }

    .controls {
        flex-direction: column;
    }

    .control-button {
        width: 100%;
    }
}

@media (prefers-reduced-motion: reduce) {
    .welcome-heart {
        animation: none;
    }
}
// Quiz Fragen-Bank
const questionBank = [
    {"id": 1, "category": "Vertrieb", "difficulty": "easy", "question": "Welche Hauptaufgabe hat ein Immobilienberater im Verkauf?", "answers": ["Nur Fotos erstellen", "Eigentümer und Käufer durch den Vermittlungsprozess begleiten", "Nur Mietverträge verwalten", "Bauarbeiten überwachen"], "correct": 1, "explanation": "Die Beratung umfasst Akquise, Bewertung, Vermarktung, Besichtigungen, Verhandlung und Begleitung bis zum Abschluss."},
    {"id": 2, "category": "Akquise", "difficulty": "easy", "question": "Was bedeutet Objektakquise?", "answers": ["Gewinnung neuer Immobilien zur Vermarktung", "Renovierung eines Hauses", "Prüfung der Bonität", "Erstellung eines Grundbuchs"], "correct": 0, "explanation": "Bei der Objektakquise gewinnt der Berater neue Eigentümer und Vermarktungsaufträge."},
    {"id": 3, "category": "Vertrieb", "difficulty": "medium", "question": "Was ist ein qualifizierter Alleinauftrag?", "answers": ["Mehrere Makler vermarkten parallel", "Der Makler wird exklusiv beauftragt und der Eigentümer verweist Interessenten an ihn", "Der Käufer muss sofort bezahlen", "Ein Auftrag ohne Laufzeit"], "correct": 1, "explanation": "Der qualifizierte Alleinauftrag regelt eine exklusive Zusammenarbeit zwischen Eigentümer und Makler."},
    {"id": 4, "category": "Bewertung", "difficulty": "easy", "question": "Was ist der Verkehrswert einer Immobilie?", "answers": ["Der ursprüngliche Kaufpreis", "Ein unter gewöhnlichen Umständen am Markt erzielbarer Wert", "Nur der Bodenwert", "Die Restschuld"], "correct": 1, "explanation": "Der Verkehrswert orientiert sich am üblichen Geschäftsverkehr und wertrelevanten Merkmalen."},
    {"id": 5, "category": "Bewertung", "difficulty": "medium", "question": "Welche drei klassischen Wertermittlungsverfahren gibt es?", "answers": ["Sachwert-, Ertragswert- und Vergleichswertverfahren", "Miet-, Kauf- und Pachtverfahren", "Bank-, Notar- und Steuerverfahren", "Boden-, Dach- und Kellerverfahren"], "correct": 0, "explanation": "Vergleichs-, Ertrags- und Sachwertverfahren sind die drei klassischen Bewertungsansätze."},
    {"id": 6, "category": "Bewertung", "difficulty": "medium", "question": "Wann ist das Vergleichswertverfahren besonders geeignet?", "answers": ["Bei gut vergleichbaren Wohnungen oder Grundstücken", "Nur bei Fabriken", "Nur bei denkmalgeschützten Häusern", "Wenn keine Marktdaten vorhanden sind"], "correct": 0, "explanation": "Das Verfahren nutzt Preise hinreichend vergleichbarer Immobilien."},
    {"id": 7, "category": "Bewertung", "difficulty": "medium", "question": "Wofür wird das Ertragswertverfahren häufig verwendet?", "answers": ["Bei renditeorientierten und vermieteten Immobilien", "Nur bei Ferienhäusern", "Für Möbel", "Für Straßen"], "correct": 0, "explanation": "Bei vermieteten Objekten steht der nachhaltig erzielbare Ertrag im Fokus."},
    {"id": 8, "category": "Bewertung", "difficulty": "medium", "question": "Worauf stellt das Sachwertverfahren besonders ab?", "answers": ["Auf Herstellungskosten der baulichen Anlagen und den Bodenwert", "Nur auf die Monatsmiete", "Nur auf Käufernachfrage", "Nur auf den Energieausweis"], "correct": 0, "explanation": "Der Sachwert leitet sich aus Bodenwert und Wert der baulichen Anlagen ab."},
    {"id": 9, "category": "Markt", "difficulty": "easy", "question": "Was beschreibt der Bodenrichtwert?", "answers": ["Einen durchschnittlichen Lagewert des Bodens", "Die Gebäudeversicherung", "Die maximale Maklerprovision", "Den Mietspiegel"], "correct": 0, "explanation": "Der Bodenrichtwert ist ein Orientierungswert für Grund und Boden in einer Richtwertzone."},
    {"id": 10, "category": "Markt", "difficulty": "easy", "question": "Welche Faktoren beeinflussen den Immobilienwert besonders?", "answers": ["Lage, Zustand, Größe und Marktsituation", "Nur die Wandfarbe", "Nur das Alter des Eigentümers", "Nur die Anzahl der Fotos"], "correct": 0, "explanation": "Objekt- und marktbezogene Faktoren prägen den Wert."},
    {"id": 11, "category": "Marketing", "difficulty": "easy", "question": "Was ist ein Exposé?", "answers": ["Eine strukturierte Präsentation der Immobilie", "Ein Kaufvertrag", "Ein Grundbuchauszug", "Eine Baugenehmigung"], "correct": 0, "explanation": "Das Exposé informiert Interessenten über wesentliche Angaben zur Immobilie."},
    {"id": 12, "category": "Marketing", "difficulty": "medium", "question": "Was sollte ein gutes Exposé vermeiden?", "answers": ["Klare Grundrisse", "Irreführende oder unbelegte Aussagen", "Professionelle Bilder", "Transparente Eckdaten"], "correct": 1, "explanation": "Objektangaben sollten korrekt und nachvollziehbar sein."},
    {"id": 13, "category": "Marketing", "difficulty": "easy", "question": "Was ist bei Immobilienfotos besonders wichtig?", "answers": ["Eine helle, realistische und aufgeräumte Darstellung", "Starke Verzerrung", "Verbergen aller Mängel", "Nur Außenaufnahmen"], "correct": 0, "explanation": "Gute Bilder sind realistisch und attraktiv, ohne einen falschen Eindruck zu erzeugen."},
    {"id": 14, "category": "Marketing", "difficulty": "easy", "question": "Was bedeutet Home Staging?", "answers": ["Gezielte optische Vorbereitung einer Immobilie für die Vermarktung", "Technische Gebäudeprüfung", "Änderung des Grundbuchs", "Finanzierungsberatung"], "correct": 0, "explanation": "Home Staging verbessert die Präsentation durch Möblierung, Licht und Gestaltung."},
    {"id": 15, "category": "Besichtigung", "difficulty": "medium", "question": "Was ist bei einer Besichtigung am sinnvollsten?", "answers": ["Bedarf kennen und das Objekt strukturiert präsentieren", "Kritische Fragen vermeiden", "Nur den Preis nennen", "Keine Unterlagen mitbringen"], "correct": 0, "explanation": "Vorbereitung, Bedarfsorientierung und Transparenz sind wichtig."},
    {"id": 16, "category": "Vertrieb", "difficulty": "medium", "question": "Wie geht ein professioneller Berater mit einem erkennbaren Mangel um?", "answers": ["Verschweigen", "Transparent ansprechen und sachlich einordnen", "Beschönigen", "Dem Käufer die Schuld geben"], "correct": 1, "explanation": "Transparenz stärkt Vertrauen und reduziert spätere Konflikte."},
    {"id": 17, "category": "Recht", "difficulty": "easy", "question": "Was ist ein Grundbuchauszug?", "answers": ["Nachweis über rechtliche Verhältnisse an einem Grundstück", "Möbelliste", "Energieverbrauchsrechnung", "Maklerrechnung"], "correct": 0, "explanation": "Das Grundbuch dokumentiert Eigentum, Rechte und Belastungen."},
    {"id": 18, "category": "Recht", "difficulty": "hard", "question": "In welcher Grundbuchabteilung stehen typischerweise die Eigentumsverhältnisse?", "answers": ["Abteilung I", "Abteilung II", "Abteilung III", "Im Energieausweis"], "correct": 0, "explanation": "In Abteilung I werden Eigentümer und Grundlagen der Eintragung geführt."},
    {"id": 19, "category": "Recht", "difficulty": "hard", "question": "Was findet sich typischerweise in Abteilung III des Grundbuchs?", "answers": ["Grundpfandrechte wie Grundschulden", "Hausordnung", "Energieklasse", "Wohnflächenberechnung"], "correct": 0, "explanation": "Abteilung III enthält Hypotheken, Grundschulden und ähnliche Rechte."},
    {"id": 20, "category": "Recht", "difficulty": "easy", "question": "Was ist eine Grundschuld?", "answers": ["Ein Grundpfandrecht zur Kreditsicherung", "Eine kommunale Steuer", "Eine Mietkaution", "Ein Baumangel"], "correct": 0, "explanation": "Grundschulden dienen Banken als Sicherheit bei Immobilienkrediten."},
    {"id": 21, "category": "Energie", "difficulty": "easy", "question": "Was ist ein Energieausweis?", "answers": ["Ein Dokument mit energetischen Kennwerten eines Gebäudes", "Eigentumsnachweis", "Baugenehmigung", "Mietvertrag"], "correct": 0, "explanation": "Der Energieausweis informiert über energetische Eigenschaften eines Gebäudes."},
    {"id": 22, "category": "Energie", "difficulty": "hard", "question": "Was unterscheidet Bedarfsausweis und Verbrauchsausweis?", "answers": ["Berechneter Energiebedarf gegenüber gemessenem Verbrauch", "Kauf gegenüber Miete", "Wohnung gegenüber Haus", "Altbau gegenüber Neubau"], "correct": 0, "explanation": "Der Bedarfsausweis ist berechnet, der Verbrauchsausweis basiert auf Verbrauchsdaten."},
    {"id": 23, "category": "Wohnungseigentum", "difficulty": "hard", "question": "Was ist eine Teilungserklärung?", "answers": ["Sie regelt die Aufteilung in Sonder- und Gemeinschaftseigentum", "Sie teilt den Kaufpreis auf", "Sie regelt nur die Provision", "Sie ist ein Mietvertrag"], "correct": 0, "explanation": "Die Teilungserklärung legt bei Wohnungseigentum die Rechte an Gebäudeteilen fest."},
    {"id": 24, "category": "Wohnungseigentum", "difficulty": "easy", "question": "Was ist Gemeinschaftseigentum?", "answers": ["Gebäudeteile, die allen Wohnungseigentümern gemeinsam gehören", "Nur die Einbauküche", "Nur der private Stellplatz", "Private Möbel"], "correct": 0, "explanation": "Dazu gehören etwa tragende Bauteile und gemeinschaftlich genutzte Flächen."},
    {"id": 25, "category": "Wirtschaft", "difficulty": "easy", "question": "Was ist eine Instandhaltungsrücklage?", "answers": ["Finanzielles Polster der Eigentümergemeinschaft für Maßnahmen", "Mietkaution", "Maklerhonorar", "Notargebühr"], "correct": 0, "explanation": "Die Rücklage deckt zukünftige Erhaltungsmaßnahmen am Gemeinschaftseigentum."},
    {"id": 26, "category": "Protokolle", "difficulty": "hard", "question": "Warum sind Protokolle der Eigentümerversammlung wichtig?", "answers": ["Sie zeigen Beschlüsse, Konflikte und geplante Maßnahmen", "Sie ersetzen den Kaufvertrag", "Sie bestimmen automatisch den Marktpreis", "Sie dienen nur der Werbung"], "correct": 0, "explanation": "Protokolle geben Auskunft über Beschlüsse, Arbeiten und mögliche Kosten."},
    {"id": 27, "category": "Finanzen", "difficulty": "easy", "question": "Was ist Hausgeld?", "answers": ["Regelmäßige Zahlung für gemeinschaftliche Kosten", "Maklercourtage", "Grunderwerbsteuer", "Kaufpreisrate"], "correct": 0, "explanation": "Hausgeld deckt laufende Gemeinschaftskosten und Zuführungen zur Rücklage."},
    {"id": 28, "category": "Finanzen", "difficulty": "hard", "question": "Was bedeutet Mietrendite vereinfacht?", "answers": ["Verhältnis von Mietertrag zum eingesetzten Kaufpreis", "Miete plus Nebenkosten", "Differenz zwischen Wohn- und Nutzfläche", "Höhe der Mietkaution"], "correct": 0, "explanation": "Renditekennzahlen setzen Erträge in Beziehung zum Kaufpreis oder Kapital."},
    {"id": 29, "category": "Risiko", "difficulty": "easy", "question": "Was bedeutet Leerstandsrisiko?", "answers": ["Risiko ausbleibender Mieten bei unvermieteten Flächen", "Risiko eines leeren Kellers", "Risiko hoher Notarkosten", "Risiko fehlender Fotos"], "correct": 0, "explanation": "Leerstand mindert Einnahmen und kann zusätzliche Kosten erzeugen."},
    {"id": 30, "category": "Due Diligence", "difficulty": "hard", "question": "Was bedeutet Due Diligence beim Immobilienkauf?", "answers": ["Systematische Prüfung rechtlicher, wirtschaftlicher und technischer Aspekte", "Nur eine Besichtigung", "Nur Preisverhandlung", "Nur Finanzierungsanfrage"], "correct": 0, "explanation": "Due Diligence prüft Chancen, Risiken und Unterlagen strukturiert."},
    {"id": 31, "category": "Prozess", "difficulty": "easy", "question": "Wer beurkundet in Deutschland regelmäßig einen Grundstückskaufvertrag?", "answers": ["Ein Notar oder eine Notarin", "Der Makler allein", "Die Hausverwaltung", "Der Bankberater"], "correct": 0, "explanation": "Grundstückskaufverträge werden regelmäßig notariell beurkundet."},
    {"id": 32, "category": "Recht", "difficulty": "hard", "question": "Was ist die Auflassung?", "answers": ["Die dingliche Einigung über den Eigentumsübergang", "Kündigung eines Mietvertrags", "Löschung eines Exposés", "Übergabe der Möbel"], "correct": 0, "explanation": "Die Auflassung ist die Einigung über den Eigentumsübergang am Grundstück."},
    {"id": 33, "category": "Recht", "difficulty": "easy", "question": "Wann wird ein Käufer typischerweise Eigentümer einer Immobilie?", "answers": ["Mit der Eintragung im Grundbuch", "Mit der ersten Besichtigung", "Mit der Finanzierungsanfrage", "Allein mit der Schlüsselübergabe"], "correct": 0, "explanation": "Der Eigentumsübergang erfolgt regelmäßig mit Eintragung ins Grundbuch."},
    {"id": 34, "category": "Finanzen", "difficulty": "easy", "question": "Was ist die Grunderwerbsteuer?", "answers": ["Steuer auf den Erwerb eines Grundstücks oder einer Immobilie", "Jährliche Gebäudeversicherung", "Maklerhonorar", "Mietnebenkosten"], "correct": 0, "explanation": "Die Grunderwerbsteuer fällt bei einem steuerbaren Grundstückserwerb an."},
    {"id": 35, "category": "Finanzen", "difficulty": "hard", "question": "Was gehört typischerweise zu den Kaufnebenkosten?", "answers": ["Grunderwerbsteuer, Notar, Grundbuch und gegebenenfalls Maklerkosten", "Nur Stromkosten", "Nur Renovierung", "Nur Umzug"], "correct": 0, "explanation": "Kaufnebenkosten entstehen zusätzlich zum Kaufpreis."},
    {"id": 36, "category": "Finanzen", "difficulty": "hard", "question": "Wozu dient eine Finanzierungsbestätigung?", "answers": ["Sie kann die wirtschaftliche Umsetzbarkeit plausibilisieren", "Sie ersetzt den Notarvertrag", "Sie garantiert den Objektwert", "Sie ersetzt den Energieausweis"], "correct": 0, "explanation": "Sie hilft, die Finanzierungssituation eines Interessenten einzuordnen."},
    {"id": 37, "category": "Verhandlung", "difficulty": "easy", "question": "Was ist ein Kaufpreisangebot?", "answers": ["Erklärung eines Interessenten, zu welchem Preis er kaufen möchte", "Automatisch der notarielle Kaufvertrag", "Eine Grundschuld", "Eine Mietbürgschaft"], "correct": 0, "explanation": "Ein Kaufpreisangebot ist Teil der Verhandlung."},
    {"id": 38, "category": "Verhandlung", "difficulty": "hard", "question": "Was ist bei Preisverhandlungen besonders wichtig?", "answers": ["Interessen verstehen, Fakten verwenden und ruhig moderieren", "Sofort maximal nachgeben", "Druck ohne Argumente", "Mängel leugnen"], "correct": 0, "explanation": "Gute Verhandlung verbindet Vorbereitung, Marktargumente und wertschätzende Kommunikation."},
    {"id": 39, "category": "Markt", "difficulty": "medium", "question": "Was ist ein realistischer Angebotspreis?", "answers": ["Ein Preis, der Objektmerkmale und Marktlage berücksichtigt", "Immer der höchste Preis im Internet", "Nur der Wunschpreis", "Immer genau der Bodenrichtwert"], "correct": 0, "explanation": "Ein marktgerechter Preis basiert auf Daten, Lage, Objektqualität und Nachfrage."},
    {"id": 40, "category": "Marketing", "difficulty": "medium", "question": "Warum kann ein deutlich überhöhter Angebotspreis schaden?", "answers": ["Er kann Nachfrage reduzieren und Vermarktung verlängern", "Er erhöht automatisch den Marktwert", "Er senkt Nebenkosten", "Er ersetzt Marketing"], "correct": 0, "explanation": "Ein zu hoher Preis kann geeignete Interessenten abschrecken."},
    {"id": 41, "category": "Leads", "difficulty": "hard", "question": "Was bedeutet Lead-Qualifizierung?", "answers": ["Prüfung von Bedarf, Ernsthaftigkeit, Zeitpunkt und finanziellen Rahmenbedingungen", "Löschen aller Anfragen", "Nur Versand eines Exposés", "Sofortiger Notartermin"], "correct": 0, "explanation": "Qualifizierung ermöglicht zielgerichtete Betreuung."},
    {"id": 42, "category": "Bedarfsermittlung", "difficulty": "easy", "question": "Welche Frage eignet sich gut zur Bedarfsermittlung bei Käufern?", "answers": ["Welche Lage, Größe, Nutzung und welches Budget suchen Sie?", "Warum kaufen Sie nicht sofort?", "Welche Wandfarbe mögen alle?", "Kennen Sie den Eigentümer?"], "correct": 0, "explanation": "Offene, strukturierte Fragen helfen, ein klares Suchprofil zu erstellen."},
    {"id": 43, "category": "Kundenpflege", "difficulty": "easy", "question": "Was bedeutet After-Sales im Immobilienvertrieb?", "answers": ["Betreuung nach Abschluss und Pflege der Kundenbeziehung", "Nur Werbung vor Akquise", "Bewertung ohne Auftrag", "Technische Bauabnahme"], "correct": 0, "explanation": "Gute Nachbetreuung fördert Empfehlungen und langfristige Beziehungen."},
    {"id": 44, "category": "Markt", "difficulty": "medium", "question": "Warum sind lokale Marktkenntnisse wichtig?", "answers": ["Für realistische Bewertung, Zielgruppenansprache und Beratung", "Nur für den Arbeitsweg", "Damit keine Unterlagen nötig sind", "Sie sind nicht wichtig"], "correct": 0, "explanation": "Mikrolage, Infrastruktur und Nachfrage beeinflussen Bewertung und Beratung."},
    {"id": 45, "category": "Akquise", "difficulty": "hard", "question": "Was ist bei Kaltakquise grundsätzlich wichtig?", "answers": ["Rechtliche Vorgaben beachten und professionell vorgehen", "Jede Person jederzeit ungefragt anrufen", "Einwilligungen ignorieren", "Falsche Empfehlungen nennen"], "correct": 0, "explanation": "Akquise sollte wirksam, respektvoll und rechtssicher erfolgen."},
    {"id": 46, "category": "Persönlichkeitsprofil", "difficulty": "easy", "question": "Welche Eigenschaft ist für selbstständige Immobilienberater besonders wichtig?", "answers": ["Eigenmotivation und strukturierte Arbeitsweise", "Auf Zufallskunden warten", "Netzwerke vermeiden", "Feedback ablehnen"], "correct": 0, "explanation": "Eigenverantwortung, Planung und Eigenmotivation sind zentral."},
    {"id": 47, "category": "Premiumservice", "difficulty": "hard", "question": "Was zeigt Dienstleistungsorientierung im Premiumsegment?", "answers": ["Verbindlichkeit, Diskretion, Erreichbarkeit und individuelle Beratung", "Nur teure Kleidung", "Wenig Kundenkontakt", "Standardantworten"], "correct": 0, "explanation": "Premiumservice lebt von Vertrauen, Qualität und persönlicher Betreuung."},
    {"id": 48, "category": "Einstieg", "difficulty": "medium", "question": "Welche Aussage passt besonders gut zu einem Quereinsteiger?", "answers": ["Vorkenntnisse sind immer zwingend", "Vertriebsleidenschaft, Lernbereitschaft und Kundenorientierung sind wichtig", "Nur Baukenntnisse zählen", "Netzwerkaufbau ist unwichtig"], "correct": 1, "explanation": "Quereinsteiger überzeugen mit Kommunikationsfähigkeit und Lernbereitschaft."},
    {"id": 49, "category": "Prozess", "difficulty": "easy", "question": "Welche Aufgaben können zum gesamten Immobilienverkaufsprozess gehören?", "answers": ["Von Objektakquise bis Notartermin und Übergabe", "Nur das erste Telefonat", "Nur Fotografieren", "Nur Hausverwaltung"], "correct": 0, "explanation": "Ein Immobilienberater begleitet oft den kompletten Vermarktungsprozess."},
    {"id": 50, "category": "Vorstellungsgespräch", "difficulty": "easy", "question": "Welche Antwort wirkt als Quereinsteiger überzeugend?", "answers": ["Ich benötige keine Einarbeitung", "Ich bringe Kundenkompetenz mit und baue mein Wissen systematisch auf", "Ich möchte wenig Akquise", "Mich interessieren nur Besichtigungen"], "correct": 1, "explanation": "Eine überzeugende Antwort verbindet vorhandene Fähigkeiten mit Lernbereitschaft."},
    {"id": 51, "category": "Vertrieb", "difficulty": "easy", "question": "Was ist das wichtigste Ziel im Vertrieb?", "answers": ["Kundenbedarf erkennen und passende Lösungen anbieten", "Möglichst viele Anrufe", "Produkte auswendig kennen", "Rabatte verteilen"], "correct": 0, "explanation": "Erfolgreicher Vertrieb beginnt mit dem Verständnis der Kundenbedürfnisse."},
    {"id": 52, "category": "Vertrieb", "difficulty": "easy", "question": "Was ist eine Bedarfsanalyse?", "answers": ["Ermittlung von Wünschen, Zielen und Anforderungen", "Analyse der Konkurrenz", "Berechnung der Provision", "Immobilienbewertung"], "correct": 0, "explanation": "Gezielte Fragen machen die Bedürfnisse des Kunden sichtbar."},
    {"id": 53, "category": "Vertrieb", "difficulty": "easy", "question": "Warum sind offene Fragen im Vertrieb wichtig?", "answers": ["Kunden geben mehr Informationen", "Sie werden schneller beantwortet", "Nur Ja oder Nein ist möglich", "Sie erhöhen den Preis"], "correct": 0, "explanation": "Offene Fragen helfen, Motive und Bedürfnisse zu verstehen."},
    {"id": 54, "category": "Vertrieb", "difficulty": "medium", "question": "Was versteht man unter Einwandbehandlung?", "answers": ["Professioneller Umgang mit Bedenken", "Ablehnung aller Fragen", "Sofortiger Preisnachlass", "Beendigung des Gesprächs"], "correct": 0, "explanation": "Einwände sollten sachlich geklärt werden."},
    {"id": 55, "category": "Vertrieb", "difficulty": "medium", "question": "Wie reagiert ein guter Verkäufer auf einen Preiseinwand?", "answers": ["Er fragt nach Hintergründen und argumentiert den Mehrwert", "Er beendet das Gespräch", "Er gibt maximalen Rabatt", "Er ignoriert ihn"], "correct": 0, "explanation": "Der Fokus sollte auf Nutzen und Mehrwert liegen."},
    {"id": 56, "category": "Vertrieb", "difficulty": "medium", "question": "Was bedeutet Abschlussorientierung?", "answers": ["Den Kunden professionell zur Entscheidung begleiten", "Unter Druck setzen", "Ungeprüft unterschreiben lassen", "Auf Rückmeldung verzichten"], "correct": 0, "explanation": "Abschlussorientierung ist zielgerichtete, kundenorientierte Gesprächsführung."},
    {"id": 57, "category": "Akquise", "difficulty": "medium", "question": "Was ist bei der Neukundenakquise besonders wichtig?", "answers": ["Regelmäßigkeit und Konsequenz", "Nur auf Empfehlungen warten", "Wenig Kontakt", "Nur E-Mails"], "correct": 0, "explanation": "Kontinuierliche Akquise ist eine Grundlage erfolgreichen Vertriebs."},
    {"id": 58, "category": "Akquise", "difficulty": "hard", "question": "Was ist die typische Reihenfolge eines Verkaufsgesprächs?", "answers": ["Kontaktaufbau, Bedarfsanalyse, Präsentation, Einwandbehandlung, Abschluss", "Preis, Vertrag, Abschluss", "Abschluss, Bedarf, Präsentation", "Exposé senden und warten"], "correct": 0, "explanation": "Diese Gesprächsstruktur ist ein verbreitetes Grundmodell."},
    {"id": 59, "category": "Vertrieb", "difficulty": "hard", "question": "Warum kaufen Kunden häufig nicht beim günstigsten Anbieter?", "answers": ["Vertrauen, Kompetenz und Service sind ebenfalls entscheidend", "Hohe Preise sind immer besser", "Rabatte sind verboten", "Der Preis ist unwichtig"], "correct": 0, "explanation": "Neben dem Preis beeinflussen Vertrauen, Kompetenz und Service die Entscheidung."},
    {"id": 60, "category": "Vertrieb", "difficulty": "hard", "question": "Welche Eigenschaft ist für gute Verkäufer besonders wichtig?", "answers": ["Empathie und aktives Zuhören", "Möglichst viel reden", "Nur Fachwissen", "Konflikte vermeiden"], "correct": 0, "explanation": "Gute Verkäufer verstehen Motive und hören aktiv zu."},
    {"id": 61, "category": "Kaltakquise", "difficulty": "easy", "question": "Was ist das Hauptziel eines ersten Kaltakquisegesprächs?", "answers": ["Sofort Vertrag abschließen", "Interesse wecken und nächsten Schritt vereinbaren", "Möglichst lange sprechen", "Direkt Rabatt anbieten"], "correct": 1, "explanation": "Im Erstkontakt geht es um Relevanz, Bedarf und einen nächsten Schritt."},
    {"id": 62, "category": "Kaltakquise", "difficulty": "easy", "question": "Was ist bei der Vorbereitung besonders wichtig?", "answers": ["Informationen über Zielgruppe und Bedarf sammeln", "Langen Monolog vorbereiten", "Nur Provision berechnen", "Auf Fragen verzichten"], "correct": 0, "explanation": "Vorbereitung ermöglicht eine bedarfsorientierte Ansprache."},
    {"id": 63, "category": "Kaltakquise", "difficulty": "easy", "question": "Wie sollte der Gesprächseinstieg wirken?", "answers": ["Klar, freundlich und relevant", "Aggressiv", "Unsicher und ausführlich", "Unpersönlich"], "correct": 0, "explanation": "Ein klarer Einstieg vermittelt Professionalität."},
    {"id": 64, "category": "Kaltakquise", "difficulty": "easy", "question": "Warum ist aktives Zuhören wichtig?", "answers": ["Damit weniger Vorbereitung nötig ist", "Damit Bedürfnisse, Motive und Einwände erkannt werden", "Damit das Gespräch endet", "Damit keine Fragen kommen"], "correct": 1, "explanation": "Aktives Zuhören hilft, die Kundensituation zu verstehen."},
    {"id": 65, "category": "Kaltakquise", "difficulty": "easy", "question": "Welche Frage eignet sich für den Erstkontakt?", "answers": ["Wann unterschreiben Sie?", "Welche Überlegungen haben Sie aktuell zu Ihrer Immobilie?", "Warum haben Sie uns nicht beauftragt?", "Wie hoch ist Ihr Vermögen?"], "correct": 1, "explanation": "Eine offene Frage lädt zur Beschreibung der Situation ein."},
    {"id": 66, "category": "Kaltakquise", "difficulty": "easy", "question": "Was kann ein Nein im Erstgespräch bedeuten?", "answers": ["Nie wieder ansprechen", "Der Verkäufer hat versagt", "Ein Nein zum Zeitpunkt oder aktuellen Angebot", "Immer Wunsch nach Rabatt"], "correct": 2, "explanation": "Ein Nein kann unterschiedliche Ursachen haben und ist respektvoll zu behandeln."},
    {"id": 67, "category": "Kaltakquise", "difficulty": "easy", "question": "Was sollte nach einem erfolgreichen Erstkontakt passieren?", "answers": ["Keine weitere Bearbeitung", "Konkreten nächsten Schritt vereinbaren und dokumentieren", "Täglich Nachrichten senden", "Sofort Vertrag schicken"], "correct": 1, "explanation": "Ein nächster Schritt schafft Verbindlichkeit."},
    {"id": 68, "category": "Kaltakquise", "difficulty": "medium", "question": "Was ist ein Nutzenargument?", "answers": ["Beschreibung des konkreten Vorteils für den Kunden", "Aufzählung aller Eigenschaften", "Interne Kennzahl", "Forderung an den Kunden"], "correct": 0, "explanation": "Ein Nutzenargument zeigt den konkreten Mehrwert."},
    {"id": 69, "category": "Kaltakquise", "difficulty": "medium", "question": "Wie reagieren, wenn ein Eigentümer aktuell nicht verkaufen möchte?", "answers": ["Entscheidung akzeptieren und passenden Folgekontakt anbieten", "Sofort erneut anrufen", "Marktwert zu hoch ansetzen", "Entscheidung kritisieren"], "correct": 0, "explanation": "Respekt erhält die Beziehung für einen möglichen späteren Kontakt."},
    {"id": 70, "category": "Kaltakquise", "difficulty": "medium", "question": "Warum sollte eine Akquiseansprache individuell sein?", "answers": ["Damit sie länger dauert", "Damit der Kunde Relevanz erkennt", "Damit keine Analyse nötig ist", "Damit sofort Provision Thema ist"], "correct": 1, "explanation": "Individualität zeigt Vorbereitung und Relevanz."},
    {"id": 71, "category": "Kaltakquise", "difficulty": "medium", "question": "Was ist bei der Nachverfolgung wichtig?", "answers": ["Mehrfach täglich anrufen", "Vereinbarungen einhalten und Anlass nennen", "Immer dieselbe Nachricht", "Sofort aufgeben"], "correct": 1, "explanation": "Professionelle Nachverfolgung ist verbindlich und relevant."},
    {"id": 72, "category": "Kaltakquise", "difficulty": "medium", "question": "Was beschreibt eine gute Akquiseroutine?", "answers": ["Nur bei freier Zeit", "Regelmäßig planen, durchführen und auswerten", "Nur spontane Anrufe", "Nach Ablehnung einstellen"], "correct": 1, "explanation": "Planung und Auswertung verbessern langfristig die Ergebnisse."},
    {"id": 73, "category": "Kaltakquise", "difficulty": "hard", "question": "Ein Eigentümer sagt: „Schicken Sie Informationen." Was ist sinnvoll?", "answers": ["Standardprospekt ohne Fragen", "Relevante Informationen klären und Folgetermin vereinbaren", "Versand ablehnen", "Sofort Vertrag senden"], "correct": 1, "explanation": "Bedarfsklärung macht Informationen relevant und der Folgetermin schafft Verbindlichkeit."},
    {"id": 74, "category": "Einwandbehandlung", "difficulty": "easy", "question": "Was ist ein Einwand im Verkaufsgespräch?", "answers": ["Frage, Sorge oder Hinderungsgrund", "Immer endgültige Ablehnung", "Vertragsabschluss", "Provisionsabrechnung"], "correct": 0, "explanation": "Ein Einwand zeigt offene Fragen oder Unsicherheiten."},
    {"id": 75, "category": "Einwandbehandlung", "difficulty": "easy", "question": "Wie sollte man grundsätzlich auf einen Einwand reagieren?", "answers": ["Zuhören, Verständnis zeigen und nachfragen", "Unterbrechen", "Ignorieren", "Direkt widersprechen"], "correct": 0, "explanation": "Professionelle Einwandbehandlung beginnt mit Zuhören."},
    {"id": 76, "category": "Einwandbehandlung", "difficulty": "easy", "question": "Warum sollte ein Einwand nicht persönlich genommen werden?", "answers": ["Er drückt oft sachliche oder emotionale Unsicherheiten aus", "Der Kunde hat immer recht", "Einwände sind unwichtig", "Jedes Gespräch endet im Abschluss"], "correct": 0, "explanation": "Einwände gehören zum Verkaufsprozess."},
    {"id": 77, "category": "Einwandbehandlung", "difficulty": "easy", "question": "Welche Reaktion auf „Das ist mir zu teuer" ist sinnvoll?", "answers": ["Sofort reduzieren", "Fragen, womit verglichen wird und was wichtig ist", "Gespräch beenden", "Unverständnis vorwerfen"], "correct": 1, "explanation": "Eine Rückfrage klärt den tatsächlichen Preiseinwand."},
    {"id": 78, "category": "Einwandbehandlung", "difficulty": "medium", "question": "Was unterscheidet Einwand und Vorwand?", "answers": ["Einwand ist tatsächliches Hindernis, Vorwand verdeckt möglicherweise den Grund", "Kein Unterschied", "Vorwand ist bindend", "Einwand betrifft nur Preis"], "correct": 0, "explanation": "Respektvolle Rückfragen helfen, den tatsächlichen Grund zu erkennen."},
    {"id": 79, "category": "Einwandbehandlung", "difficulty": "medium", "question": "„Ich möchte darüber nachdenken." Wie reagiert man?", "answers": ["Fragen, welcher Punkt noch offen ist", "Zur Unterschrift drängen", "Kommentarlos beenden", "Sofort Rabatt anbieten"], "correct": 0, "explanation": "Die Rückfrage zeigt, welche Entscheidungsgrundlage fehlt."},
    {"id": 80, "category": "Einwandbehandlung", "difficulty": "medium", "question": "„Ich kenne bereits einen Makler." Welche Antwort passt?", "answers": ["Dann kann ich nicht helfen", "Was ist Ihnen bei der Zusammenarbeit besonders wichtig?", "Der Makler ist ungeeignet", "Beenden Sie die Zusammenarbeit"], "correct": 1, "explanation": "Die Antwort respektiert die Beziehung und öffnet die Bedarfsklärung."},
    {"id": 81, "category": "Einwandbehandlung", "difficulty": "medium", "question": "Wie reagiert man auf „Ihre Provision ist zu hoch"?", "answers": ["Sofort halbieren", "Nachfragen und Leistungsumfang sowie Mehrwert erläutern", "Ignorieren", "Provision streichen"], "correct": 1, "explanation": "Zuerst wird der Hintergrund geklärt, danach der Mehrwert erläutert."},
    {"id": 82, "category": "Einwandbehandlung", "difficulty": "medium", "question": "Was ist eine Rückfrage in der Einwandbehandlung?", "answers": ["Gezielte Frage zum Hintergrund", "Wiederholung des Preises", "Aufforderung zur Unterschrift", "Ablehnung des Kundenwunsches"], "correct": 0, "explanation": "Rückfragen verhindern vorschnelle Antworten."},
    {"id": 83, "category": "Einwandbehandlung", "difficulty": "hard", "question": "„Ich verkaufe lieber selbst." Welche Reaktion ist geeignet?", "answers": ["Das funktioniert nicht", "Welche Vorteile versprechen Sie sich davon und welche Aufgaben möchten Sie übernehmen?", "Dann gibt es keinen Marktpreis", "Privatverkauf ist unmöglich"], "correct": 1, "explanation": "Die offene Frage wertet nicht ab und klärt Motivation und Bedarf."},
    {"id": 84, "category": "Einwandbehandlung", "difficulty": "hard", "question": "Der Eigentümer verlangt einen deutlich überhöhten Preis. Was tun?", "answers": ["Ungeprüft übernehmen", "Mit Marktdaten argumentieren, Folgen erläutern und Strategie entwickeln", "Immer ablehnen", "Wunschpreis garantieren"], "correct": 1, "explanation": "Professionelle Beratung verbindet Wünsche mit belastbaren Marktdaten."},
    {"id": 85, "category": "Einwandbehandlung", "difficulty": "hard", "question": "Was sollte nach der Beantwortung eines Einwands erfolgen?", "answers": ["Gespräch beenden", "Prüfen, ob der Einwand geklärt ist, dann nächsten Schritt vereinbaren", "Einwand wiederholen", "Automatisch Rabatt geben"], "correct": 1, "explanation": "Eine Kontrollfrage zeigt, ob noch Bedenken bestehen."}
];
// Quiz Application Logic
const DIFFICULTY_LEVELS = ['easy', 'medium', 'hard'];
const DIFFICULTY_NAMES = {
    easy: 'Leicht',
    medium: 'Mittel',
    hard: 'Schwer'
};

// Constants
const TOTAL_QUESTIONS = 85;
const TIME_PER_QUESTION = 20;
const TIME_BONUS_PER_SECOND = 5;
const BASE_POINTS = 100;
const STREAK_TO_LEVEL_UP = 6;
const INITIAL_LIVES = 3;

// Game State
let gameState = {
    remainingQuestions: [],
    askedQuestions: [],
    currentQuestion: null,
    questionNumber: 0,
    score: 0,
    lives: INITIAL_LIVES,
    timeLeft: TIME_PER_QUESTION,
    timerInterval: null,
    answerLocked: false,
    correctStreak: 0,
    currentDifficultyIndex: 0,
    keyHandler: null
};

// DOM Elements
const $ = (id) => document.getElementById(id);

const elements = {
    startScreen: $('startScreen'),
    game: $('game'),
    startButton: $('startButton'),
    nextButton: $('nextButton'),
    restartButton: $('restartButton'),
    position: $('position'),
    level: $('level'),
    score: $('score'),
    lives: $('lives'),
    highscore: $('highscore'),
    progress: $('progress'),
    timer: $('timer'),
    question: $('question'),
    meta: $('meta'),
    answers: $('answers'),
    feedback: $('feedback')
};

// Local Storage Management
function getHighscore() {
    return Number(localStorage.getItem('immobilienQuizHighscore') || 0);
}

function saveHighscore() {
    if (gameState.score > getHighscore()) {
        localStorage.setItem('immobilienQuizHighscore', String(gameState.score));
    }
    elements.highscore.textContent = getHighscore();
}

// Utility Functions
function shuffleArray(arr) {
    const a = [...arr];
    for (let i = a.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [a[i], a[j]] = [a[j], a[i]];
    }
    return a;
}

function getNextQuestion() {
    const wanted = DIFFICULTY_LEVELS[gameState.currentDifficultyIndex];
    let pool = gameState.remainingQuestions.filter(q => q.difficulty === wanted);
    
    if (!pool.length) {
        pool = [...gameState.remainingQuestions];
    }
    
    if (!pool.length) return null;
    
    const selected = pool[Math.floor(Math.random() * pool.length)];
    gameState.remainingQuestions = gameState.remainingQuestions.filter(q => q.id !== selected.id);
    return selected;
}

// Game Flow
function startGame() {
    clearInterval(gameState.timerInterval);
    removeKeyListener();
    
    gameState.remainingQuestions = [...questionBank];
    gameState.askedQuestions = [];
    gameState.questionNumber = 0;
    gameState.score = 0;
    gameState.lives = INITIAL_LIVES;
    gameState.correctStreak = 0;
    gameState.currentDifficultyIndex = 0;
    gameState.answerLocked = false;
    
    elements.startScreen.hidden = true;
    elements.game.hidden = false;
    elements.restartButton.style.display = 'none';
    elements.nextButton.style.display = 'none';
    elements.progress.style.width = '0%';
    elements.highscore.textContent = getHighscore();
    
    loadNextQuestion();
}

function loadNextQuestion() {
    gameState.currentQuestion = getNextQuestion();
    if (!gameState.currentQuestion) {
        finishGame(true);
        return;
    }
    gameState.askedQuestions.push(gameState.currentQuestion);
    showQuestion();
}

function showQuestion() {
    clearInterval(gameState.timerInterval);
    removeKeyListener();
    gameState.answerLocked = false;
    gameState.timeLeft = TIME_PER_QUESTION;
    gameState.questionNumber++;
    
    updateStats();
    
    elements.feedback.textContent = 'Wähle eine Antwort.';
    elements.question.textContent = gameState.currentQuestion.question;
    elements.meta.textContent = `Kategorie: ${gameState.currentQuestion.category}`;
    
    renderAnswers();
    
    elements.nextButton.style.display = 'none';
    elements.answers.querySelector('.answer')?.focus();
    
    updateTimerDisplay();
    
    gameState.timerInterval = setInterval(() => {
        gameState.timeLeft--;
        updateTimerDisplay();
        if (gameState.timeLeft <= 0) handleTimeout();
    }, 1000);
    
    setupKeyListener();
}

function renderAnswers() {
    elements.answers.innerHTML = '';
    const shuffled = shuffleArray(
        gameState.currentQuestion.answers.map((text, originalIndex) => ({
            text,
            originalIndex
        }))
    );
    
    shuffled.forEach((item, i) => {
        const btn = document.createElement('button');
        btn.type = 'button';
        btn.className = 'answer';
        btn.textContent = `${i + 1}. ${item.text}`;
        btn.dataset.correct = String(item.originalIndex === gameState.currentQuestion.correct);
        btn.setAttribute('role', 'listitem');
        btn.addEventListener('click', () => selectAnswer(btn));
        elements.answers.appendChild(btn);
    });
}

function updateStats() {
    elements.position.textContent = `${gameState.questionNumber}/${TOTAL_QUESTIONS}`;
    elements.level.textContent = `${DIFFICULTY_NAMES[DIFFICULTY_LEVELS[gameState.currentDifficultyIndex]]} · Serie ${gameState.correctStreak}/${STREAK_TO_LEVEL_UP}`;
    elements.score.textContent = gameState.score;
    elements.lives.textContent = '❤️'.repeat(gameState.lives);
}

function setupKeyListener() {
    gameState.keyHandler = (e) => {
        if (gameState.answerLocked) return;
        const idx = Number(e.key) - 1;
        const buttons = [...elements.answers.querySelectorAll('.answer')];
        if (idx >= 0 && idx < buttons.length) buttons[idx].click();
    };
    document.addEventListener('keydown', gameState.keyHandler);
}

function removeKeyListener() {
    if (gameState.keyHandler) {
        document.removeEventListener('keydown', gameState.keyHandler);
        gameState.keyHandler = null;
    }
}

function updateTimerDisplay() {
    elements.timer.textContent = `Zeit: ${gameState.timeLeft} Sekunden`;
    elements.timer.className = gameState.timeLeft <= 5 ? 'timer-warning' : '';
}

// Answer Handling
function selectAnswer(selected) {
    if (gameState.answerLocked) return;
    gameState.answerLocked = true;
    clearInterval(gameState.timerInterval);
    removeKeyListener();
    
    const buttons = [...elements.answers.querySelectorAll('.answer')];
    buttons.forEach(b => {
        b.disabled = true;
        if (b.dataset.correct === 'true') b.classList.add('correct');
    });
    
    if (selected.dataset.correct === 'true') {
        handleCorrectAnswer();
    } else {
        handleWrongAnswer(selected);
    }
    
    updateAfterAnswer();
}

function handleCorrectAnswer() {
    const earned = BASE_POINTS + gameState.timeLeft * TIME_BONUS_PER_SECOND;
    gameState.score += earned;
    gameState.correctStreak++;
    
    let msg = '';
    if (gameState.correctStreak >= STREAK_TO_LEVEL_UP && 
        gameState.currentDifficultyIndex < DIFFICULTY_LEVELS.length - 1) {
        gameState.currentDifficultyIndex++;
        gameState.correctStreak = 0;
        msg = `<br><br>🚀 <strong>Neue Schwierigkeit: ${DIFFICULTY_NAMES[DIFFICULTY_LEVELS[gameState.currentDifficultyIndex]]}!</strong>`;
    }
    
    elements.feedback.innerHTML = 
        `✅ <strong>Richtig!</strong> +${earned} Punkte<br>${gameState.currentQuestion.explanation}${msg}`;
}

function handleWrongAnswer(selected) {
    gameState.lives--;
    gameState.correctStreak = 0;
    selected.classList.add('wrong');
    elements.feedback.innerHTML = 
        `❌ <strong>Leider nicht richtig.</strong><br>${gameState.currentQuestion.explanation}<br><br>Deine Serie wurde zurückgesetzt.`;
}

function handleTimeout() {
    if (gameState.answerLocked) return;
    gameState.answerLocked = true;
    clearInterval(gameState.timerInterval);
    removeKeyListener();
    
    gameState.lives--;
    gameState.correctStreak = 0;
    
    const buttons = [...elements.answers.querySelectorAll('.answer')];
    buttons.forEach(b => {
        b.disabled = true;
        if (b.dataset.correct === 'true') b.classList.add('correct');
    });
    
    elements.feedback.innerHTML = 
        `⏰ <strong>Die Zeit ist abgelaufen.</strong><br>${gameState.currentQuestion.explanation}<br><br>Deine Serie wurde zurückgesetzt.`;
    
    updateAfterAnswer();
}

function updateAfterAnswer() {
    updateStats();
    elements.progress.style.width = `${gameState.questionNumber / TOTAL_QUESTIONS * 100}%`;
    saveHighscore();
    
    if (gameState.lives <= 0) {
        finishGame(false);
    } else {
        elements.nextButton.style.display = 'inline-block';
        elements.nextButton.focus();
    }
}

function goToNextQuestion() {
    if (gameState.questionNumber >= TOTAL_QUESTIONS) {
        finishGame(true);
    } else {
        loadNextQuestion();
    }
}

// Game End
function finishGame(completed) {
    clearInterval(gameState.timerInterval);
    removeKeyListener();
    gameState.answerLocked = true;
    saveHighscore();
    
    elements.answers.innerHTML = '';
    elements.meta.textContent = '';
    
    if (completed) {
        elements.question.textContent = '🏆 Alle 85 Fragen geschafft!';
    } else {
        elements.question.textContent = 'Game Over';
    }
    
    elements.feedback.innerHTML = `
        <strong>Dein Ergebnis</strong><br><br>
        Punkte: <strong>${gameState.score}</strong><br>
        Beantwortete Fragen: ${gameState.questionNumber} von ${TOTAL_QUESTIONS}<br>
        Erreichte Schwierigkeit: ${DIFFICULTY_NAMES[DIFFICULTY_LEVELS[gameState.currentDifficultyIndex]]}<br>
        Highscore: ${getHighscore()}<br><br>
        <small>Die Inhalte dienen ausschließlich der Gesprächsvorbereitung.</small>
    `;
    
    elements.progress.style.width = `${gameState.questionNumber / TOTAL_QUESTIONS * 100}%`;
    elements.nextButton.style.display = 'none';
    elements.restartButton.style.display = 'inline-block';
    elements.restartButton.focus();
}

// Event Listeners
elements.startButton.addEventListener('click', startGame);
elements.nextButton.addEventListener('click', goToNextQuestion);
elements.restartButton.addEventListener('click', startGame);

// Initialize
elements.highscore.textContent = getHighscore();
