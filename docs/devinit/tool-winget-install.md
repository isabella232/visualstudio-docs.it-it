---
title: winget-install
description: Strumento devinit per winget.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4adc65b8e9e3bdd9587c11df83fe86d20c2eff27ad8f05cc6a510e539eddd920
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239449"
---
# <a name="winget-install"></a>winget-install

> [!IMPORTANT]
> A partire dal 12 aprile 2021, la connessione a GitHub Codespaces da Visual Studio 2019 non sarà più supportata e questa anteprima privata è stata conclusa. L'attenzione è rivolta alle esperienze in continua evoluzione per un ciclo interno basato sul cloud e soluzioni VDI ottimizzate per un'ampia gamma di carichi di lavoro Visual Studio cloud. Nell'ambito di `devinit` questo e degli strumenti associati non saranno più disponibili. Si consiglia di partecipare al forum della community degli sviluppatori per Visual Studio informazioni sulle anteprime future e informazioni sulla roadmap.

Lo `winget-install` strumento viene usato per installare i pacchetti [winget](https://docs.microsoft.com/windows/package-manager/winget/).

## <a name="usage"></a>Utilizzo

Se entrambe `input` le proprietà e vengono `additionalOptions` omesse o vuote, lo strumento restituirà un errore.

| Nome                                         | Tipo   | Obbligatoria | valore                                                                             |
|----------------------------------------------|--------|----------|-----------------------------------------------------------------------------------|
| **Commenti**                                 | stringa | No       | Proprietà comments facoltativa. Non usato.                                             |
| [**Input**](#input)                          | stringa | No       | Pacchetto da installare. Per informazioni [dettagliate,](#input) vedere Input di seguito.                    |
| [**additionalOptions**](#additional-options) | stringa | No       | Per [informazioni dettagliate, vedere](#additional-options) Opzioni aggiuntive di seguito.                  |

### <a name="input"></a>Input

La proprietà di input viene usata per specificare `Id` o del pacchetto da `Name` installare, ad esempio 'MongoDB.Server'. Il valore di input verrà aggiunto a un `winget install` comando (ad esempio `winget install MongoDB.Server` ). Se il nome del pacchetto non è univoco e corrisponde ad altri pacchetti, è possibile specificare il del pacchetto e aggiungere il flag a per assicurarsi che l'identità del pacchetto `Id` `--exact` corrisponda `additionalOptions` esattamente. `Id`L'oggetto di un pacchetto può essere trovato eseguendo il comando e usando il parametro per un `winget search` `Id` pacchetto.  

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile passare opzioni di configurazione aggiuntive come valore di additionalOptions. Questi argomenti sono pass-through diretto agli argomenti usati da `winget install` e sono definiti nella `winget install` [documentazione](https://docs.microsoft.com/windows/package-manager/winget/install)di .

#### <a name="manifests"></a>Manifesti

Un elemento facoltativo `winget` aggiuntivo che supporta è la possibilità di fornire un file [manifesto](https://docs.microsoft.com/windows/package-manager/winget/install#local-install) per specificare in dettaglio il pacchetto da installare. Per usare questa funzionalità con devinit, il parametro deve essere vuoto e la proprietà deve includere l'opzione seguita dal percorso `input` del manifesto , ad esempio `additionalOptions` `--manifest` `--manifest path.to.manifest.yml` .

### <a name="built-in-options"></a>Opzioni predefinite

Lo strumento winget-install imposta una serie di argomenti della riga di comando winget per garantire che winget possa essere eseguito senza testa. Questi argomenti sono elencati di seguito e la relativa documentazione è disponibile nella `winget install` [documentazione](https://docs.microsoft.com/windows/package-manager/winget/install)di .

| Nome     | Descrizione                                                                                                                       |
|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| --silent | Esegue il programma di installazione in modalità invisibile all'utente, senza visualizzare alcuna interfaccia utente. L'esperienza predefinita mostra lo stato del programma di installazione.                       | 

## <a name="example-usage"></a>Esempio di utilizzo

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "run": [
        {
            "comments": "Installs Microsoft PowerToys.",
            "tool": "winget-install",
            "input": "Microsoft.PowerToys",
            "additionalOptions": "--version 0.15.2",
        },
        {
            "comments": "Installs PostgreSQL.",
            "tool": "winget-install",
            "input": "PostgreSQL.PostgreSQL",
            "additionalOptions": "--exact"
        },
        {
            "comments": "Installs the package defined in winget-manifest.yml.",
            "tool": "winget-install",
            "additionalOptions": "--manifest winget-manifest.yml"
        }
    ]
}
```
