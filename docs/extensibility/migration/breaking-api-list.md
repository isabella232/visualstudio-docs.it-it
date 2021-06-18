---
title: Modifiche di rilievo dell'API in Visual Studio 2022 Preview
description: Informazioni sulle modifiche dell'API che causano la mancata compilazione delle estensioni di Visual Studio esistenti durante la migrazione delle estensioni Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308730"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Modifiche di rilievo all'API in Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Se si esegue la migrazione di un'estensione a Visual Studio 2022, le modifiche di rilievo elencate di seguito potrebbero influire sull'utente.

## <a name="reference-assemblies-no-longer-installed"></a>Assembly di riferimento non più installati

È possibile che molti degli assembly a cui si fa riferimento che MSBuild risolto da una directory Visual Studio di installazione non sia più installato. È consigliabile usare NuGet per acquisire gli assembly Visual Studio SDK necessari. Per [informazioni dettagliate su questa operazione,](update-visual-studio-extension.md#modernize-your-vsix-project) vedere Modernizzare i progetti.

## <a name="removed-apis"></a>API rimosse

Nel Visual Studio 2022 sono state rimosse una serie di API nell'ambito dello spostamento Visual Studio futuro. Un elenco delle API rimosse è disponibile nella pagina [Elenco DELLE API](removed-api-list.md) rimosse.

## <a name="interop-breaking-changes"></a>Modifiche di rilievo dell'interoperabilità

Molte DELLE API sono state modificate in Visual Studio 2022, in genere con semplici modifiche che sono semplici da adattare al codice.

Per gestire le modifiche di rilievo, si prevede di fornire un nuovo meccanismo per la distribuzione degli assembly di interoperabilità. In particolare, per Visual Studio 2022 e oltre viene fornito un singolo assembly di interoperabilità con definizioni per molte interfacce pubbliche Visual Studio comune. Tale assembly contiene definizioni gestite per molte interfacce Visual Studio che si allontanano da più assembly di interoperabilità. Il nuovo assembly di interoperabilità viene distribuito tramite il `Microsoft.VisualStudio.Interop` pacchetto NuGet.

Tuttavia, Visual Studio componenti usati principalmente in contesti nativi e con un numero ridotto di modifiche di rilievo continueranno ad avere i propri assembly di interoperabilità ( ad esempio, l'assembly del debugger sarà ancora VisualStudio.Debugger.Interop.dll come attualmente). In ogni caso, è possibile fare riferimento agli assembly dall'applicazione così come sono attualmente.

Si tratta di una modifica significativa e significa che le estensioni che usano API in e assembly compilati in questo nuovo approccio non sono compatibili con le versioni precedenti di Visual Studio che usano l'assembly di interoperabilità precedente.

Ciò offre alcuni vantaggi molto importanti che semplificano l'aggiornamento dell'estensione Visual Studio 2022:

- Eventuali API interrotte diventeranno errori in fase di compilazione, semplificando la ricerca e la correzione.
- È necessario aggiornare solo il codice che usa un'API interrotta in Visual Studio 2022.
- Non sarà possibile usare accidentalmente l'API precedente, ora interrotta.

In generale, queste modifiche avranno come risultato una versione più stabile Visual Studio per tutti gli utenti. Lo svantaggio principale di questo approccio è che gli assembly gestiti non potranno essere eseguiti in Visual Studio 2019 e Visual Studio 2022 senza compilare il codice una volta per ogni versione di Visual Studio di destinazione.

Quando si verificano errori di compilazione a causa delle differenze delle API tra Visual Studio 2019 e Visual Studio 2022, è possibile trovare l'API o il modello elencato di seguito con indicazioni su come risolverlo.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` o `uint` dove `IntPtr` è previsto

Si prevede che si tratta di un errore molto comune. Per rendere Visual Studio 2022 un processo a 64 bit, alcune DELLE API di interoperabilità dove si presuppone che un puntatore possa rientrare in un intero a 32 bit per usare effettivamente un valore di dimensioni del puntatore.

Errore di esempio:

> Argomento 3: impossibile convertire da 'out uint' a 'out System.IntPtr'

È sufficiente aggiornare il codice in modo che sia previsto o fornito o dove o `IntPtr` `UIntPtr` usato per risolvere `int` `uint` l'interruzione.

Correzione di esempio:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>Tipo di interoperabilità definito in due assembly

Quando il compilatore C# segnala un errore che indica che un tipo in uso è definito in due assembly, è probabile che si faccia riferimento a un assembly dalla versione Visual Studio 2019 dell'SDK a cui non è più necessario fare riferimento.

Errore di esempio:

> errore CS0433: Il tipo 'IVsDpiAware' esiste sia in 'Microsoft.VisualStudio.Interop, Version=17.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' e 'Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

Fare riferimento alla tabella [di mapping degli assembly](migrated-assemblies.md) di riferimento per vedere quale nome di assembly è il nome preferito in Visual Studio 2022.
Considerando i due assembly denominati nell'errore di esempio precedente e esaminando questa tabella, si noti `Microsoft.VisualStudio.Interop` che è il nuovo nome dell'assembly. La correzione sarebbe quindi la rimozione del riferimento `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` a dal progetto.

In alcuni casi è disponibile un pacchetto Visual Studio versione 2022 per l'assembly deprecato che contiene i server d'inoltro dei tipi. Quando questa opzione è disponibile,  è possibile aggiornare il riferimento al pacchetto alla versione Visual Studio 2022 anziché rimuoverlo. I server d'inoltro dei tipi risolveranno l'errore dal compilatore.

Tenere presente che a volte questi riferimenti possono essere relativi a riferimenti transitivi al pacchetto e quindi possono essere più difficili da rimuovere rispetto a un riferimento diretto creato nel file di progetto. In questi casi, assicurarsi che tutti i riferimenti diretti ai pacchetti utilizzino tutti Visual Studio 2022 SDK. È possibile fare *riferimentoproject.assets.jssu* per identificare la catena di pacchetti responsabili dell'uso dell'assembly deprecato. L'aggiornamento di un riferimento transitivo a un pacchetto Visual Studio 2022 è semplice quanto installarlo come riferimento diretto.

Se non è possibile modificare l'albero delle dipendenze, ad esempio perché implica una dipendenza di terze parti, è possibile aggiungere un riferimento diretto al pacchetto precedente a Visual Studio 2022 e aggiungere metadati a tale elemento per risolvere l'errore del `ExcludeAssets="compile"` `PackageReference` compilatore. Tenere tuttavia presente che con questa tecnica, l'estensione può mantenere una dipendenza da un assembly pre-Visual Studio 2022 e l'estensione potrebbe non funzionare correttamente in fase di esecuzione.

### <a name="missing-reference-to-an-interop-assembly"></a>Riferimento mancante a un assembly di interoperabilità

Quando si fa riferimento a un assembly compilato in base all'SDK Visual Studio 2022, è possibile che venga visualizzato un errore che indica la mancanza di un riferimento all'assembly.

Errore di esempio:

> Errore CS0012 Il tipo 'IVsTextViewFilter' è definito in un assembly a cui non viene fatto riferimento. È necessario aggiungere un riferimento all'assembly 'Microsoft.VisualStudio.TextManager.Interop, Version=7.1.40304.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

Usando la [tabella di modifica del mapping dell'assembly](migrated-assemblies.md)di riferimento , è possibile verificare che l'assembly richiesto non sia di fatto un assembly a cui è necessario fare riferimento.

La correzione migliore è l'aggiornamento della dipendenza a una versione compilata con l'SDK di Visual Studio 2022 in modo che l'assembly di interoperabilità rimosso non venga più richiesto dal compilatore.

In alcuni casi è disponibile un pacchetto Visual Studio versione 2022 per l'assembly deprecato che contiene i server d'inoltro dei tipi. Quando questa opzione è disponibile, è possibile aggiungere un riferimento al pacchetto alla versione Visual Studio 2022 del pacchetto obsoleto in modo che i server d'inoltro dei tipi risolvono l'errore dal compilatore.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` manca

Esistono due definizioni di questa interfaccia, in due spazi dei nomi. Solo uno di questi era destinato all'utilizzo gestito.

spazio dei nomi Visual Studio 2019 | Spazio dei nomi Visual Studio 2022 | Uso previsto
--|--|--
Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Utilizzo del codice gestito
Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.COMAsyncServiceProvider.IAsyncServiceProvider | solo interoperabilità di basso livello

Se viene visualizzato un errore su , è possibile che sia stato utilizzato quello destinato al `IAsyncServiceProvider` codice nativo (la seconda riga). 
In questo caso, è possibile eseguire l'aggiornamento al nuovo spazio dei nomi o passare all'interfaccia più semplice da gestire.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` e `_DTE` errori di cast di tipo

`DTE` e `_DTE` sono entrambe interfacce. Uno deriva dall'altro. Tuttavia, Visual Studio 2022, i tipi di base e derivati vengono scambiati.
In questo modo alcune assegnazioni di tipi o cast hanno esito negativo.

Ciò significa anche dove si usava `new DTE()` , ora è necessario usare `new _DTE()` .

### <a name="missing-argument-on-a-method-invocation"></a>Argomento mancante nella chiamata a un metodo

Alcuni metodi non dichiarano più argomenti predefiniti per i parametri facoltativi nell'API di interoperabilità.
Se si verifica un errore relativo a un argomento mancante per una chiamata di interoperabilità COM e il parametro chiama per un tipo, il valore predefinito precedente definito dall'API di interoperabilità di Visual Studio 2019 potrebbe essere , quindi è consigliabile aggiungere come argomento per risolvere l'errore di `object` `""` `""` compilazione.

In caso di dubbi su quale fosse l'argomento predefinito, provare a cambiare il contesto del servizio di linguaggio da Visual Studio 2022 a Visual Studio 2019 in modo da ottenere Intellisense con gli assembly di interoperabilità meno recenti per visualizzare l'argomento predefinito e quindi aggiungerlo in modo esplicito al codice. Continuerà a funzionare correttamente se compilato per Visual Studio 2019, ma verrà ora compilato per Visual Studio 2022.

Correzione di esempio:

```diff
-process4.Attach2();
+process4.Attach2("");
```
