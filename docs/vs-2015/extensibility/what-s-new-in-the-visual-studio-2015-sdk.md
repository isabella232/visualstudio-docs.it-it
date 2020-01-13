---
title: Novità di Visual Studio 2015 SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d47e40a5c38eeb7898aa179282fa55bbe17ef1d5
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917327"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>&#39;Novità di Visual Studio 2015 SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2015, Visual Studio 2015 aggiornato e Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

A partire da Visual Studio 2017, l'analisi dei modelli di progetto e di elemento personalizzati non verrà più eseguita. L'estensione deve invece fornire file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione utilizzando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere [upgrade Custom Modelli di progetti ed elementi per Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Lo schema del manifesto del modello è documentato in [riferimenti allo schema del manifesto del modello di Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>VS 2015 SDK Update 1
 L'aggiornamento 1 include gli strumenti che consentono all'estensione di funzionare bene con i temi di colore e il servizio immagini di Visual Studio.

 Questi argomenti sono disponibili nella sezione [utilità VSSDK](../extensibility/internals/vssdk-utilities.md) :

- Gli [strumenti](../extensibility/internals/color-theming-tools.md) per la colorazione dei colori consentono di creare e modificare colori personalizzati per Visual Studio.

- Gli [strumenti del servizio immagini](../extensibility/internals/image-service-tools.md) consentono di lavorare con i file manifesto dell'immagine di Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nuovo modo per aggiungere Visual Studio SDK a Visual Studio
 A partire da Visual Studio 2015, non è necessario scaricare Visual Studio SDK separatamente. È invece possibile installarla come parte del normale processo di installazione oppure è possibile scegliere di installarla in un secondo momento. Quando si apre o si crea una soluzione VSIX, in Visual Studio viene richiesto di installare il Visual Studio Extensibility Tools. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Nuove modalità di creazione di estensioni
 A partire da Visual Studio 2015 SDK, sono disponibili diverse opzioni per la creazione di estensioni, a seconda del linguaggio di programmazione in uso.

### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic
 Per C# e Visual Basic, esiste una gamma completa di modelli di elementi di progetto che consentono di creare pacchetti VSPackage, comandi di menu, finestre degli strumenti, classificatori di editor, aree di lavoro dell'editor ed estensioni dei margini dell'editor. È possibile aggiungere uno o tutti questi al progetto VSIX standard. Per altre informazioni, vedere:

- [Creazione di un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Creazione di un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     La procedura guidata VSPackage non crea più estensioni C# in o Visual Basic.

### <a name="c"></a>C++
 Per C++, i comandi di menu, le finestre degli strumenti e gli editor personalizzati sono supportati dalla procedura guidata VSPackage. Cercarla nella finestra di dialogo **nuovo progetto** in **Visual C++ /Extensibility**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assembly di riferimento di Visual Studio SDK tramite NuGet
 Per migliorare la portabilità e la condivisione di progetti di estendibilità, è possibile usare le versioni NuGet degli assembly di riferimento di Visual Studio SDK.  Questi sono disponibili in [NuGet.org](https://www.nuget.org/) pubblicati da [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) e possono essere facilmente aggiunti al progetto o alla soluzione tramite la finestra di dialogo riferimenti di Visual Studio **/Gestisci pacchetti NuGet** . È possibile aggiungere singoli riferimenti a assembly di estensibilità specifici o aggiungere contemporaneamente tutti gli assembly di riferimento di Visual Studio SDK usando il [metapacchetto](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)di vs SDK. Per altre informazioni su NuGet, vedere [Panoramica di NuGet](/nuget/) e [gestire i pacchetti NuGet usando la finestra di dialogo](/nuget/consume-packages/install-use-packages-visual-studio).

 Quando si usano le versioni NuGet degli assembly di riferimento di Visual Studio SDK, un altro utente non deve installare l'SDK di Visual Studio per aprire e compilare il progetto.  Gli assembly di riferimento NuGet e gli strumenti di compilazione di Visual Studio SDK verranno installati automaticamente nel computer per il progetto.

 I modelli di elemento di Visual Studio SDK usano NuGet per i riferimenti e gli strumenti di compilazione, in modo da ottenere i vantaggi di NuGet per impostazione predefinita.

> [!NOTE]
> È possibile continuare a usare gli assembly di riferimento di VS SDK installati con i progetti (che si trovano in \<percorso di installazione di Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e non è necessario aggiornare i progetti di estensibilità esistenti per usare i pacchetti NuGet.  La finestra di dialogo riferimenti al progetto **/Aggiungi riferimento** continua a usare gli assembly di riferimento di vs SDK installati.
>
> Per modificare i progetti esistenti per l'uso di NuGet, vedere [procedura: eseguire la migrazione dei pacchetti VSPackage a Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) che include una sezione sull'aggiornamento di progetti di estendibilità ai pacchetti NuGet.

## <a name="light-bulbs"></a>Lampadine
 Uno dei nuovi modi più interessanti per scrivere codice di estensione è fornito dal progetto Roslyn. Per ulteriori informazioni, vedere [Roslyn](https://github.com/dotnet/Roslyn).

 Le lampadine sono una nuova funzionalità fornita con VSSDK. Sono icone usate nell'editor di Visual Studio che si espandono per visualizzare un set di azioni di refactoring del codice o correzioni per i problemi identificati dagli analizzatori di codice predefiniti. Per altre informazioni, vedere [Walkthrough: Displaying Light Bulb suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Linee guida sull'esperienza utente aggiornate
 Progettazione di nuove estensioni o funzionalità per Visual Studio Vedere le linee guida aggiornate ed espanse sull' [esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Sono disponibili i [token di colore](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), le [dimensioni dei caratteri](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), le specifiche del layout di finestra di [dialogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e altre linee guida necessarie per integrare facilmente la nuova interfaccia utente con Visual Studio.
