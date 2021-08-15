---
title: Risoluzione dei problemi relativi al ricaricamento rapido XAML
description: Risolvere i problemi che possono verificarsi con Ricaricamento rapido XAML.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 02090956026e6359313534666237bcddd614f4ce3addfdc600d1a7f0289ed9d6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440180"
---
# <a name="troubleshooting-xaml-hot-reload"></a>Risoluzione dei problemi relativi al ricaricamento rapido XAML

Questa guida alla risoluzione dei problemi include istruzioni dettagliate che dovrebbero risolvere la maggior parte dei problemi che impediscono Ricaricamento rapido XAML funzioni correttamente.

Ricaricamento rapido XAML è supportato per le app WPF e UWP. Per informazioni dettagliate sui requisiti del sistema operativo e degli strumenti, vedere Scrivere ed eseguire il debug di [codice XAML con](xaml-hot-reload.md)Ricaricamento rapido XAML .

## <a name="hot-reload-is-not-available"></a>Ricaricamento rapido non è disponibile

Se viene visualizzato il messaggio "Ricaricamento rapido disponibile" sulla barra degli strumenti in-app durante il debug dell'app, seguire le istruzioni descritte in questo articolo per risolvere il problema.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>Verificare che la Ricaricamento rapido XAML sia abilitata

La funzionalità è abilitata per impostazione predefinita. Quando si avvia il debug dell'app, assicurarsi di visualizzare la barra degli strumenti in-app, che conferma che Ricaricamento rapido XAML è disponibile:

![Ricaricamento rapido XAML disponibili](../debugger/media/xaml-hot-reload-available.png)

Se la barra degli strumenti in-app non è visualizzata, aprire **Opzioni di debug**  >    >  **Generale**. Assicurarsi che entrambe le opzioni, **Abilita strumenti di debug dell'interfaccia utente per XAML** e **Abilita** Ricaricamento rapido XAML selezionate.

![Screenshot della finestra Visual Studio Opzioni di debug. Le opzioni Di debug generale sono selezionate e l'opzione Ricaricamento rapido XAML selezionata.](../debugger/media/xaml-hot-reload-enable.png)

Se queste opzioni sono selezionate, passare alla struttura ad albero visuale live **(** Debug Windows Live Visual Tree ) e assicurarsi che il pulsante Mostra strumenti di runtime nella barra degli strumenti dell'applicazione (all'estrema sinistra) sia  >    >  selezionato. 

![Screenshot della barra degli strumenti nella parte superiore della finestra Albero visuale live con il pulsante "Mostra strumenti di runtime nell'applicazione" selezionato.](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Verificare di usare Avvia debug anziché Collega a processo

Ricaricamento rapido XAML richiede che la variabile di `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ambiente sia impostata su 1 al momento dell'avvio dell'applicazione. Visual Studio imposta automaticamente come parte del **comando Debug**  >  **Avvia** debug **(o F5).** Se invece si vuole usare Ricaricamento rapido XAML con il **comando Esegui** debug connessione  >  **a** processo, impostare la variabile di ambiente manualmente.

> [!NOTE]
> Per impostare una variabile di ambiente, usare il pulsante Start per cercare "variabile di ambiente" e scegliere **Modifica le variabili di ambiente di sistema**. Nella finestra di dialogo visualizzata scegliere **Variabili di** ambiente , quindi aggiungerla come variabile utente e impostare il valore su `1` . Per eseguire la pulizia, rimuovere la variabile al termine del debug.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>Verificare che le MSBuild siano corrette

Per impostazione predefinita, le informazioni di origine sono incluse in una configurazione di debug. È controllato dalle proprietà MSBuild nei file di progetto, ad esempio *.csproj. Per WPF, la proprietà è `XamlDebuggingInformation` , che deve essere impostata su `True` . Per la UWP, la proprietà è `DisableXbfLineInfo` , che deve essere impostata su `False` . Esempio:

WPF:

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

Uwp:

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Verificare di usare il nome della configurazione di compilazione corretto

È necessario impostare manualmente la proprietà MSBuild per supportare Ricaricamento rapido XAML (vedere la sezione precedente) oppure usare il nome della configurazione di compilazione predefinito (Debug). Se non si imposta correttamente la proprietà MSBuild, un nome di configurazione di compilazione personalizzato non funzionerà né una build di versione.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>Verificare che il file XAML non abbia errori

Se il file XAML mostra errori **nell'Elenco errori,** Ricaricamento rapido XAML potrebbe non funzionare.

## <a name="see-also"></a>Vedi anche

[Scrivere ed eseguire il debug del codice XAML in esecuzione con Ricaricamento rapido XAML](xaml-hot-reload.md)
