---
title: API rimosse in Visual Studio 2022 Preview
description: Informazioni sulle API di VS SDK rimosse in Visual Studio 2022 Preview, per gli autori di estensioni che aggiornano le estensioni per l'Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308721"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio 2022 SDK ha rimosso le API

[!INCLUDE [preview-note](../includes/preview-note.md)]

Le API seguenti sono state rimosse da Visual Studio SDK e non possono più essere usate. Per informazioni dettagliate su come aggiornare il codice, vedere ogni sezione.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` E `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [Caricamento asincrono delle soluzioni e caricamento leggero delle soluzioni](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [Open from source safe (Apri da codice sorgente sicuro)](#open-from-source-safe)
* [Nuovo finestra di progettazione XAML WPF per .NET Framework](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

È `IVsImageService` in corso la rimozione di in Visual Studio 2022. Tutti gli utenti di `IVsImageService` devono invece passare a `IVsImageService2` .

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Se si usa `IVsImageService` , sostituire le chiamate ai relativi metodi con chiamate a metodi equivalenti in `IVsImageService2` :

| **Metodo IVsImageService** | **Metodo IVsImageService2 equivalente** |
|----------------------------|----------------------------------------|
| Add                        | AddCustomImage                         |
| Recupero                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`i metodi Add e Get di a cui si fa riferimento alle immagini personalizzate in base al nome (una stringa), anziché a un moniker.  È preferibile cambiare il codice in modo da usare solo moniker per fare riferimento a immagini personalizzate, ma se ciò risulta poco pratico sono disponibili due metodi che consentono di associare un nome a un `IVsImageService2` moniker:

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

Usando questi due metodi, è possibile continuare a fare riferimento alle immagini in base al nome.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

I `IBlockContextProvider` tipi correlati e vengono rimossi in Visual Studio 2022. Tutti gli utenti di `IBlockContextProvider` devono invece passare a `IStructureContextSourceProvider` .

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Gli utenti di `IBlockContextProvider` devono invece usare ( `IStructureContextSourceProvider` [documentazione](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)).

## <a name="itooltipprovider"></a>IToolTipProvider

I `IToolTipProvider` tipi correlati e vengono rimossi in Visual Studio 2022. Tutti gli utenti di `IToolTipProvider` devono invece passare a `IToolTipService` .

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Gli utenti di `IToolTipProvider` devono invece usare ( `IToolTipService` [documentazione](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)).

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner e IVsFullTextScanner

E `IVsTextScanner` `IVsFullTextScanner` verranno rimossi in Visual Studio 2022. Tutti gli utenti di `IVsTextScanner` o devono invece passare a `IVsFullTextScanner` `IVsTextLines` .

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Gli utenti di `IVsTextScanner` o devono usare invece ( `IVsFullTextScanner` `IVsTextLines` [documentazione](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>Caricamento asincrono delle soluzioni e caricamento leggero delle soluzioni

In Visual Studio 2022 vengono rimosse le funzionalità Caricamento soluzione asincrono (ASL) e Caricamento leggero soluzioni (LSL), di conseguenza vengono rimossi i metodi seguenti:

### <a name="interfaces"></a>Interfacce

* `IVsSolution4` - Metodi: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` - Metodi: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` - Intera interfaccia
* `IVsSolutionLoadManager` - Intera interfaccia
* `IVsSccManager3`  - Intera interfaccia
* `IVsAsynchronousProjectCreate` - Intera interfaccia
* `IVsAsynchronousProjectCreateUI` - Intera interfaccia

### <a name="enums-properties-and-ui-contexts"></a>Enumerazioni, proprietà e contesti dell'interfaccia utente

* `VSHPROPID_ProjectUnloadStatus` - Enum: `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Nessuno.

## <a name="ivsdummy"></a>IVsDummy

`IVsDummy`L'oggetto verrà rimosso in Visual Studio 2022 e non verrà sostituito. 

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Nessuno. Ma non dovrebbe avere alcun impatto perché l'API non ha fatto nulla.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft.VisualStudio.Shell.Task

La `Microsoft.VisualStudio.Shell.Task` classe è stata rinominata in in modo da non creare conflitti con la classe molto `Microsoft.VisualStudio.Shell.TaskListItem` `System.Threading.Tasks.Task` diffusa.

## <a name="open-from-source-safe"></a>Open from source safe (Apri da codice sorgente sicuro)

Il supporto per l'apertura di una soluzione dal codice sorgente sicuro viene rimosso, in quanto vengono rimossi i metodi, gli eventi e le costanti seguenti.

## <a name="interfaces"></a>Interfacce

* `IVsSCCProvider3` - Intera interfaccia

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Nessuno.

## <a name="new-wpf-xaml-designer-for-net-framework"></a>Nuovo finestra di progettazione XAML WPF per .NET Framework

L'finestra di progettazione XAML WPF corrente per .NET Framework è stato deprecato e verrà sostituito con un nuovo finestra di progettazione XAML WPF per .NET Framework, basato sulla stessa architettura usata per WPF finestra di progettazione XAML per .NET (.NET Core). Ciò significa anche che il modello di estendibilità dei controlli .NET Framework WPF basato su .design.dll e Microsoft.Windows.Design.Extensibility non è più supportato. Il nuovo finestra di progettazione XAML WPF per .NET Framework fornirà lo stesso modello di estendibilità di WPF finestra di progettazione XAML per .NET (.NET Core). Se è già stata creata un'estensione .designtools.dll per .NET (.NET Core), tale estensione funzionerà per il nuovo finestra di progettazione XAML WPF per .NET Framework. Per altre informazioni su come eseguire la migrazione al nuovo modello di estendibilità per le piattaforme WPF (.NET Framework e .NET Core) e le piattaforme UWP, vedere il collegamento alla migrazione riportato di seguito. 

### <a name="recommended-updates"></a>Aggiornamenti consigliati

Vedere [Migrazione dell'estendibilità della finestra di progettazione XAML.](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)
