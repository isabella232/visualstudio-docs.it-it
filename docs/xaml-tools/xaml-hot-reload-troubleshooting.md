---
title: Risoluzione dei problemi relativi al ricaricamento rapido XAML
description: Risolvere i problemi che possono verificarsi con il ricaricamento a caldo di XAML.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 020577cfe692d5d306a555e763d08807ab191074
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450940"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Risoluzione dei problemi relativi al ricaricamento rapido XAML

Questa guida alla risoluzione dei problemi include istruzioni dettagliate per risolvere la maggior parte dei problemi che impediscono il corretto funzionamento del ricaricamento a caldo di XAML.

Il ricaricamento a caldo di XAML è supportato per le app WPF e UWP. Per informazioni dettagliate sui requisiti del sistema operativo e degli strumenti, vedere [scrivere ed eseguire il debug di codice XAML in esecuzione con il ricaricamento a caldo di XAML](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Il ricaricamento a caldo non è disponibile

Se viene visualizzato il messaggio "ricarica a caldo non disponibile" nella barra degli strumenti in-app durante il debug dell'app, seguire le istruzioni descritte in questo articolo per risolvere il problema.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Verificare che sia abilitato il ricaricamento a caldo di XAML

La funzionalità è abilitata per impostazione predefinita. Quando si avvia il debug dell'app, assicurarsi che venga visualizzata la barra degli strumenti in-app, che conferma che è disponibile il ricaricamento a caldo di XAML:

![Ricaricamento a caldo di XAML disponibile](../debugger/media/xaml-hot-reload-available.png)

Se la barra degli strumenti in-app non è visibile, aprire **Debug** > **Opzioni** > **generale**. Assicurarsi che siano selezionate entrambe le opzioni, **Abilita strumenti di debug dell'interfaccia utente per XAML** e **Abilita ricaricamento a caldo XAML** .

![Abilita ricaricamento attivo XAML](../debugger/media/xaml-hot-reload-enable.png)

Se queste opzioni sono selezionate, passare a albero elementi visivi attivi (**Debug** > **Windows** > **albero elementi visivi attivi**) e assicurarsi che **Mostra strumenti di runtime nel** pulsante della barra degli strumenti dell'applicazione (all'estrema sinistra) sia selezionata.

![Abilita ricaricamento attivo XAML](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Verificare di usare Avvia debug anziché Connetti a processo

Il ricaricamento a caldo di XAML richiede che la variabile di ambiente `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` sia impostata su 1 al momento dell'avvio dell'applicazione. Visual Studio imposta questa impostazione automaticamente come parte del comando **debug** > **Avvia debug** (o **F5**). Se invece si vuole usare il ricaricamento a caldo di XAML con il comando **Debug** > **Connetti a processo** , impostare la variabile di ambiente manualmente.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Verificare che le proprietà di MSBuild siano corrette

Per impostazione predefinita, le informazioni sull'origine sono incluse in una configurazione di debug. Viene controllata dalle proprietà di MSBuild nei file di progetto, ad esempio *. csproj. Per WPF, la proprietà è `XamlDebuggingInformation`, che deve essere impostata su `True`. Per UWP, la proprietà è `DisableXbfLineInfo`, che deve essere impostata su `False`. Esempio:

WPF

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Verificare che sia in uso il nome della configurazione di compilazione corretta

È necessario impostare manualmente la proprietà MSBuild corretta per supportare il ricaricamento a caldo di XAML (vedere la sezione precedente) oppure è necessario utilizzare il nome predefinito della configurazione di compilazione (debug). Se la proprietà MSBuild non viene impostata correttamente, il nome di una configurazione di compilazione personalizzata non funzionerà né una build di rilascio.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Verificare che nel file XAML non siano presenti errori

Se il file XAML Mostra errori nel **Elenco errori**, il ricaricamento a caldo di XAML potrebbe non funzionare.

## <a name="see-also"></a>Vedere anche

[Scrivere ed eseguire il debug del codice XAML in esecuzione con il ricaricamento attivo XAML](xaml-hot-reload.md)
