---
title: MSI-installazione
description: strumento devinit per msiexec.
ms.date: 10/13/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 98667c602272f22e7803647a688ee75d6c6cbd70
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402315"
---
# <a name="msi-install"></a>MSI-installazione

Lo `msi-install` strumento viene usato per installare i `.msi` formati di file di pacchetto con [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

## <a name="usage"></a>Utilizzo

Se `input` viene omesso o vuoto, lo strumento restituirà un errore.

| Nome                                         | Type   | Obbligatoria | valore                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà commenti facoltativi. Non usato.                                             |
| [**input**](#input)                          | string | Sì      | Oggetto `msi` da installare. Per informazioni dettagliate, vedere l' [input](#input) riportato di seguito.                      |
| [**additionalOptions**](#additional-options) | stringa | No       | Per informazioni dettagliate, vedere le [Opzioni aggiuntive](#additional-options) seguenti.                  |

### <a name="input"></a>Input

La proprietà input viene utilizzata per specificare un percorso o un URL di un `.msi` file che verrà installato. Se il percorso di `.msi` non è corretto o l'URL non punta direttamente a un `.msi` , `msi-install` si noterà che non è possibile aprire il pacchetto di installazione.

### <a name="additional-options"></a>Opzioni aggiuntive

Le opzioni di configurazione aggiuntive possono essere passate come valore di additionalOptions. Questi argomenti sono un passthrough diretto per gli argomenti utilizzati da `msiexec` e sono definiti nella `msiexec` [documentazione](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)di.

### <a name="built-in-options"></a>Opzioni predefinite

Lo strumento MSI-install imposta una serie di `msiexec` argomenti della riga di comando per garantire che l'identità del servizio gestito possa essere eseguita. Questi argomenti sono elencati di seguito e la relativa documentazione si trova nella `msiexec` [documentazione](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)di.

| Nome          | Description                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Esegue un'installazione normale                                                                                                                                                                    | 
| /quiet        | Specifica la modalità non interattiva senza necessità di interazione dell'utente                                                                                                                                        | 
| /qn           | Specifica che non è presente alcuna interfaccia utente durante il processo di installazione                                                                                                                                           | 
| /passive      | Specifica la modalità automatica in cui l'installazione Mostra solo un indicatore di stato                                                                                                                    | 
| /l * V          | Attiva la registrazione e registra tutte le informazioni, incluse le informazioni dettagliate, in un `devinit.log` file nella cartella temporanea locale del computer. Se lo strumento ha esito negativo, viene visualizzato il percorso del file di log.      | 
| /norestart    | Arresta il riavvio del computer al termine dell'installazione, ma restituirà un codice di uscita 3010 se è necessario un riavvio                                                                  | 

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "comments": "Installs the 7-Zip MSI",
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
