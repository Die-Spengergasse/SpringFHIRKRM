# Spring FHIR

## Aufgabe
Implementiere die Entitäten [Patient](https://www.hl7.org/fhir/patient.html) und [Practitioner](https://www.hl7.org/fhir/practitionier.html) auf eine Weise dass sie mit dem FHIR-Standard kompatibel sind. Diese FHIR-Ressoucen haben auch eine vielzahl an Unterressoucen welche ebenfalls implementiert werden müssen. 

## FHIR
FHIR steht für `Fast Healthcare Interoperability Resources`. Und ist ein von [HL7](https://www.hl7.org/about/index.cfm?ref=nav) veröffentlichter Standard um Daten im Gesundheitsbereich Programmübergreifend austauschen zu können. [HL7](https://www.hl7.org/about/index.cfm?ref=nav) ist eine Organisation welche für die ANSI in den USA Standards im Gesundheitswesen entwickelt. Durch diesen Standard können alle möglichen Gesundheitsprogrammen Daten untereinander austauschen. Vielleicht auch mal deines? 


## Tests

Implementiere deinen eigenen Test der die Daten auf FHIR-Kompatibilität prüft. 

Du kannst prüfen ob die von dir generierten JSON-Daten für einen Patient passen indem du sie mit dem Beispiel von [hier](https://www.hl7.org/fhir/patient.html) vergleichst. 

Kopiere dazu die JSON-Daten aus der Dokumentation und vergleiche mittels Soll- und Ist-Wert (Expected and Actual Value).

Beispiel-Test:

```java
	@Test
	public void testCompareReturnedPatientJSONtoFHIRCompliantJSON() throws Exception {
		mockMvc
			.perform(get("/patient/1")) // get patient with id 1
			.andExpect(status().isOk()) // expect 200 HTTP status code
			.andExpect(content().json(equalTo('{"your_patient": "test_data"}'))); // returned data should be of type json and contain the same parameters as the test data
	}
```

Die initialen Testdaten sollen in der Ressourcendatei `import.sql` direkt als SQL-Statements eingefügt werden. Beim Start deines Programmes werden alle SQL-Befehle in dieser Datei ausgeführt.

### Generierung von SQL-Daten
Um zu testen ob deine SQL-Statements funktionieren kannst du sie bevor du sie in `import.sql` einfügst auch manuell ausführen. Starte dazu das Repository und gehe dann auf die Weboberfläche der H2-Datenbank. Diese erreichst du unter: http://localhost:8080/h2-console 

Wenn dein Befehl ohne Fehler ausgeführt wird kannst du ihn bedenkenlos einfügen. Beachte aber dass im Ausgangszustand dieses Projekts noch keine Entitäten angelegt wurden. Es ist also noch kein `CREATE TABLE`-Statement ausgeführt worden. 




