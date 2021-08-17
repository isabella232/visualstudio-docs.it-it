---
title: msi-install
description: Strumento devinit per msiexec.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 90f77253dacceca26691ebdac8882a1574e2eaf0877672ee04974cd58a8f5726
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390653"
---
# <a name="msi-install"></a>msi-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `msi-install` strumento viene usato per installare i formati di file dei pacchetti usando `.msi` [msiexec](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec).

## <a name="usage"></a>Utilizzo

Se viene `input` omesso o vuoto, lo strumento restituirà un errore.

| Nome                                         | Tipo   | Obbligatoria | valore                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà comments facoltativa. Non usato.                                             |
| [**Input**](#input)                          | string | Sì      | Oggetto `msi` da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito.                      |
| [**additionalOptions**](#additional-options) | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                  |

### <a name="input"></a>Input

La proprietà di input viene usata per specificare un percorso o un URL di `.msi` un file che verrà installato. Se il percorso di non è corretto o l'URL non punta direttamente a , si noterà che il pacchetto di `.msi` installazione non può essere `.msi` `msi-install` aperto.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di additionalOptions. Questi argomenti sono un pass-through diretto agli argomenti usati da `msiexec` e sono definiti nella `msiexec` [documentazione](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)di .

### <a name="built-in-options"></a>Opzioni predefinite

Lo strumento msi-install imposta una serie di argomenti della riga di comando per garantire `msiexec` che msi possa essere eseguito senza head. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella `msiexec` [documentazione](https://docs.microsoft.com/windows-server/administration/windows-commands/msiexec)di .

| Nome          | Descrizione                                                                                                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /i            | Esegue un'installazione normale                                                                                                                                                                    |
| /quiet        | Specifica la modalità non interattiva senza alcuna interazione dell'utente                                                                                                                                        |
| /qn           | Specifica che non è presente alcuna interfaccia utente durante il processo di installazione                                                                                                                                           |
| /passive      | Specifica la modalità automatica in cui l'installazione mostra solo un indicatore di stato                                                                                                                    |
| /l*V          | Attiva la registrazione e registra tutte le informazioni, incluse le informazioni dettagliate, in un file nella cartella temporanea locale `devinit.log` del computer. Se lo strumento non riesce, viene visualizzato il percorso del file di log.      |
| /norestart    | Arresta il riavvio del computer al termine dell'installazione, ma restituisce un codice di uscita 3010 se è necessario un riavvio                                                                  |

### <a name="default-behavior"></a>Comportamento predefinito

Il comportamento predefinito dello `msi-install` strumento è l'errore perché la `input` proprietà è obbligatoria.

## <a name="example-usage"></a>Esempio di utilizzo
Di seguito è riportato un esempio di come eseguire `msi-install` usando `.devinit.json` un oggetto .

#### <a name="devinitjson-that-will-install-the-7-zip-msi"></a>.devinit.jsin che installerà l'msi con 7 zip:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-4.0",
    "run": [
        {
            "tool": "msi-install",
            "input": "https://www.7-zip.org/a/7z1900.msi"
        }
    ]
}
```
