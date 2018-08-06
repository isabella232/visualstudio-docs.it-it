---
title: Cosa&#39;novità di Visual Studio 2015 SDK s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4926ed9fafb64664d3ac0426466d90611cae4450
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566693"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Cosa&#39;s novità di Visual Studio 2015 SDK
Visual Studio SDK ha le seguenti funzionalità nuove e aggiornate per Visual Studio 2015, aggiornamento di Visual Studio 2015 e Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK Update 1  
 Update 1 include strumenti che semplificano l'estensione andare bene per i temi di colore e il servizio di immagini di Visual Studio.  
  
 Questi argomenti sono sotto il [utilità VSSDK](../extensibility/internals/vssdk-utilities.md) sezione:  
  
-   Il [strumenti dei temi di colore](../extensibility/internals/color-theming-tools.md) consentono di creare e modificare i colori personalizzati per Visual Studio.  
  
-   Il [strumenti di service di immagine](../extensibility/internals/image-service-tools.md) consentono di lavorare con file manifesto di immagini di Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nuovo modo per aggiungere Visual Studio SDK per Visual Studio  
 A partire da Visual Studio 2015, non è necessario scaricare Visual Studio SDK separatamente. In alternativa, è possibile installarlo come parte del processo di installazione normale oppure è possibile scegliere di installarla in un secondo momento. Quando si apre o crea una soluzione VSIX, Visual Studio chiederà di installare Visual Studio Extensibility Tools. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nuove modalità di creazione di estensioni  
 A partire da Visual Studio 2015 SDK, sono disponibili diverse opzioni per la creazione di estensioni, a seconda del linguaggio di programmazione in uso.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic  
 Per c# e Visual Basic, sussiste una gamma completa di modelli di elemento di progetto che consentono di creare pacchetti VSPackage, i comandi di menu, finestre degli strumenti, editor classificatori, le aree di controllo dell'editor e le estensioni margine dell'editor. È possibile aggiungere uno o tutti questi modelli di progetto VSIX standard. Per altre informazioni, vedere:  
  
-   [Creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Creare un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     La creazione guidata pacchetto VSPackage non crea più estensioni in c# o Visual Basic.  
  
### <a name="c"></a>C++  
 Per C++, la creazione guidata pacchetto Visual Studio supporta i comandi di menu, finestre degli strumenti ed editor personalizzati. Cercala nella **nuovo progetto** finestra di dialogo **Visual C++ / Extensibility**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assembly di riferimento di Visual Studio SDK mediante NuGet  
 Per una migliore portabilità e la condivisione dei progetti di estendibilità, è possibile usare le versioni NuGet degli assembly di riferimento di Visual Studio SDK. Questi assembly sono disponibili nel [nuget.org](http://www.nuget.org) pubblicato da [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) e può essere facilmente aggiunto al progetto o soluzione tramite Visual Studio **fa riferimento / gestire I pacchetti NuGet** finestra di dialogo. È possibile aggiungere singoli riferimenti agli assembly di estensibilità specifica o aggiungere tutto il SDK di Visual Studio fa riferimento ad assembly in una sola volta usando Visual Studio SDK [metapacchetto](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Per altre informazioni su NuGet, vedere la [documentazione di NuGet](/NuGet) e [Package Manager UI](/NuGet/Tools/Package-Manager-UI) argomenti.  
  
 Quando si usano le versioni NuGet degli assembly di riferimento di Visual Studio SDK, un altro utente non è necessario installare il SDK di Visual Studio per aprire e compilare il progetto.  L'assembly di riferimento di NuGet e gli strumenti di compilazione di Visual Studio SDK verranno installati automaticamente nel proprio computer per il progetto.  
  
 I modelli di elemento di Visual Studio SDK usano NuGet per i relativi riferimenti e gli strumenti di compilazione in modo che si ottengono i vantaggi di NuGet per impostazione predefinita.  
  
> [!NOTE]
>  È possibile continuare a usare gli assembly di riferimento di Visual Studio SDK installati con i progetti (sotto \<percorso di installazione di Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e i progetti di estendibilità esistenti non devono essere aggiornato per usare i pacchetti NuGet.  Il progetto **fa riferimento / aggiungere riferimento** dialogo continua a usare gli assembly di riferimento di Visual Studio SDK installato.  
>   
>  Se si desidera modificare i progetti esistenti per usare NuGet, vedere [procedura: eseguire la migrazione di pacchetti VSPackage in Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) che dispone di una sezione sull'aggiornamento di progetti di estendibilità per i pacchetti NuGet.  
  
## <a name="light-bulbs"></a>Lampadine  
 Uno dei modi più interessanti nuovo della scrittura del codice di estensione viene fornito dal progetto di Roslyn. Per altre informazioni, vedere [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Le lampadine sono una nuova funzionalità che viene fornito con il SDK di pagina. Si tratta di icone utilizzate nell'editor di Visual Studio che si espandono per visualizzare un set di azioni del refactoring del codice o correzioni dei problemi identificati dagli analizzatori di codice predefiniti. Per altre informazioni, vedere [procedura dettagliata: visualizzazione di suggerimenti con lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Linee guida sull'esperienza utente aggiornata  
 Progettazione di funzionalità o le nuove estensioni per Visual Studio? Controllare l'aggiornato ed espanso [linee guida sull'esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Sono disponibili i [token di colore](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [le dimensioni dei caratteri](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specifiche del layout della finestra di dialogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e altre indicazioni necessarie per integrare facilmente la nuova interfaccia utente con Visual Studio.