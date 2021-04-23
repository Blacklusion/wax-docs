# Rewards auf WAX claimen

## Warum sollten Rewards geclaimt werden?
Dies sollte selbstverständlich sein: Für jeden produzierten Block erhält ein Blockproducer eine bestimmte Menge an Rewards (in WAX). Diese Rewards haben einen realen Wert und können entweder zum Kauf von Gegenständen in WAX verwendet oder in andere Währungen getauscht werden. Diese Rewards werden nicht automatisch auf das Konto des Blockproduzenten überwiesen, sondern müssen manuell (oder mit einem Skript) eingefordert werden. Auf WAX können GBM-Rewards auf bereits beanspruchte Producer-Rewards erhalten werden. Nicht beanspruchte Rewards bedeuten verpasste GBM-Rewards und damit verpasstes Geld.

> Die rewards sollten **regelmäßig** geclaimt werden!

## 1. Automatisch rewards claimen (empfohlen)
Das Claimen der Rewards ist eines dieser Dinge, die Sie einmal einrichten und dann einfach vergessen sollten. Daher empfehlen wir dringend, eine Art Tool oder Skript dafür zu verwenden. Es gibt Tools wie z.B. Waxy, die diese Aufgabe für Sie automatisieren. Wir haben diese Tools nicht getestet, stattdessen haben wir ein Skript auf unserer eigenen Infrastruktur eingesetzt. Dies gibt uns eine größere Kontrolle und schließlich ist es auch ziemlich einfach einzurichten. Schreiben Sie einfach selbst ein schnelles Skript oder werfen Sie einen Blick auf [unseren Code] (https://github.com/Blacklusion/claim-rewards), der über Docker deployt werden kann.

## 2. bloks.io verwenden (benutzerfreundlich)
Es gibt keinen wirklichen Grund, warum Sie Ihre Rewards manuell claimen sollten. Aber für den Fall, dass Sie es doch tun müssen, bietet bloks.io die benutzerfreundlichste Möglichkeit, dies zu tun. Gehen Sie einfach zu Ihrem EOSIO-Konto. Dann finden Sie unter Contract -> Actions eine Option für “claimrewards”. Wählen Sie diese Option und geben Sie Ihre Kontodaten ein.

![img01](/media/claim-rewards/img01.png)

## 3. Manuell über eine API / Cleos claimen
Das manuelle Ausführen einer API-Anfrage kann z. B. mit Cleos leicht durchgeführt werden. Für das Claimen von Rewards müssen Sie die folgende Aktion verwenden. Ersetzen Sie einfach actor & owner durch Ihren eigenen Kontonamen und ersetzen Sie permission durch den Namen der Berechtigung, mit der Sie sich anmelden, z. B. "active" oder vorzugsweise eine benutzerdefinierte Berechtigung wie "claimrewards".

```json
{
  account: "eosio",
  name: "claimrewards",
  authorization: [
      {
          actor: "blacklusionx",
          permission: "active",
      },
  ],
  data: {
      owner: "blacklusionx",
  },
}
```

## Ein paar Worte über Sicherheit
Unabhängig davon, wie Sie Ihre Rewards claimen wollen: Sie sollten immer eine [benutzerdefinierte Berechtigung](/de/security/custom-permissions) verwenden, die nur dem Claimen von Rewards gewidmet ist. Grundsätzlich wird die benutzerdefinierte Berechtigung nur in der Lage sein, die Aktion "claim rewards" zu signieren. Dadurch wird sichergestellt, dass keine anderen Transaktionen signiert werden können. Dies verhindert, dass Skripte oder Personen Ihrem Konto Schaden zufügen, die in den Besitz Ihres Keys gelangen.

## Wie oft sollte ich Rewards claimen?
Auf einigen EOSIO-basierten Blockchains können Sie technisch gesehen Ihre Belohnungen einfordern, wie oft Sie wollen. Auf WAX scheint dies auf einmal pro Tag beschränkt zu sein. Unserer Meinung nach ist dies eine sinnvolle Einschränkung: Abhängig von Ihren lokalen Steuergesetzen muss jeder Claim mit dem aktuellen Wechselkurs in Ihrer Steuererklärung/Jahresabschluss berücksichtigt werden. Mehr Ansprüche bedeuten mehr Aufwand bei der Erstellung Ihres Steuerberichts. Nur einmal pro Tag zu beanspruchen ist eine gute Mischung zwischen häufigem Beanspruchen und einer kleinen Anzahl von Transaktionen (~30 pro Monat), die man im Auge behalten muss. Es gibt ohnehin keinen wirklichen Grund, die Rewards häufiger zu beanspruchen.

## Hilfreiche Links
- Claim skript geschrieben in Typescript und deployt mit docker: https://github.com/Blacklusion/claim-rewards
- Waxy Claim Bot: https://waxy.io/login
