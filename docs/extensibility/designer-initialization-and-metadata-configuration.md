---
title: Inizializzazione della finestra di progettazione e configurazione dei metadati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712219"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inizializzazione della finestra di progettazione e configurazione dei metadati

La manipolazione dei metadati e degli attributi di filtro associati a una finestra di progettazione o a un componente della finestra di progettazione fornisce un meccanismo che consente alle applicazioni di definire quali strumenti vengono utilizzati da una particolare finestra di progettazione per gestire <xref:System.Type> oggetti diversi, ad esempio strutture di dati, classi o entità grafiche, quando la finestra di progettazione è disponibile e come l' **Toolbox** IDE di Visual Studio è configurato per supportare la finestra di progettazione

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]In sono disponibili diversi meccanismi per facilitare il controllo dell'inizializzazione di un componente della finestra di progettazione o di un componente della finestra di progettazione e la manipolazione dei relativi metadati da un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inizializzare i metadati e le informazioni di configurazione
 Poiché vengono caricati su richiesta, i pacchetti VSPackage potrebbero non essere stati caricati dall'ambiente Visual Studio prima della creazione di un'istanza di una finestra di progettazione. Pertanto, i pacchetti VSPackage non possono utilizzare il meccanismo standard per la configurazione di una finestra di progettazione o di un componente della finestra di progettazione alla creazione, ovvero la gestione di un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> evento Al contrario, un pacchetto VSPackage implementa un'istanza dell' <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfaccia e si registra per fornire le personalizzazioni, denominate estensioni dell'area di progettazione.

### <a name="customize-initialization"></a>Personalizza inizializzazione

La personalizzazione di una finestra di progettazione, di un componente o di un'area di progettazione comporta:

1. Modifica dei metadati della finestra di progettazione e modifica effettiva della modalità di <xref:System.Type> accesso o conversione di un determinato.

    Questa operazione viene in genere eseguita tramite i <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> meccanismi o.

    Ad esempio, quando le finestre di progettazione <xref:System.Windows.Forms> basate su vengono inizializzate, l'ambiente di Visual Studio modifica <xref:System.Drawing.Design.UITypeEditor> per <xref:System.Web.UI.WebControls.Image> gli oggetti usati con la finestra di progettazione per usare Gestione risorse per ottenere le bitmap anziché il file System.

2. Integrazione con l'ambiente, ad esempio sottoscrivendo eventi o ottenendo informazioni di configurazione del progetto. Per ottenere informazioni sulla configurazione del progetto e sottoscrivere gli eventi, è possibile ottenere l' <xref:System.ComponentModel.Design.ITypeResolutionService> interfaccia.

3. Modifica dell'ambiente utente mediante l'attivazione delle categorie appropriate della **casella degli strumenti** o la limitazione dell'applicabilità della finestra di progettazione mediante l'applicazione di un'istanza della <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe alla finestra di progettazione.

### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da un VSPackage

Un pacchetto VSPackage deve gestire l'inizializzazione della finestra di progettazione per:

1. Creazione di un oggetto che implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe non deve mai essere implementata nello stesso oggetto della <xref:Microsoft.VisualStudio.Shell.Package> classe.

2. Registrazione della classe che implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> come supporto per le estensioni della finestra di progettazione del pacchetto VSPackage. Registrare la classe applicando le istanze di  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> , <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> alla classe che fornisce l'implementazione di VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .

Ogni volta che viene creato un componente di progettazione o di progettazione, l'ambiente di Visual Studio:

- Accede a ogni provider di estensioni di superficie di progettazione registrato.

- Crea un'istanza di e Inizializza un'istanza di ogni oggetto del provider dell'estensione dell'area di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .

- Chiama ogni metodo o metodo del provider dell'estensione dell'area di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (a seconda dei casi).

Quando si implementa l' <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oggetto come membro di un VSPackage, è importante comprendere che:

- L'ambiente di Visual Studio non fornisce alcun controllo sui metadati o altre impostazioni di configurazione modificate da un particolare `DesignSurfaceExtension` provider. È possibile che due o più `DesignSurfaceExtension` provider modifichino la stessa funzionalità di progettazione in modi in conflitto, con la modifica finale definitiva. È indeterminata l'ultima modifica applicata.

- È possibile limitare in modo esplicito un'implementazione dell' <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oggetto a finestre di progettazione specifiche applicando istanze di <xref:System.ComponentModel.ToolboxItemFilterAttribute> a tale implementazione. Per ulteriori informazioni sul filtro degli elementi della **casella degli strumenti** , vedere <xref:System.ComponentModel.ToolboxItemFilterAttribute> e <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Provisioning di metadati aggiuntivi

Un pacchetto VSPackage può modificare la configurazione di una finestra di progettazione o di un componente della finestra di progettazione diverso da in fase di progettazione.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe può essere usata a livello di codice o applicata a un VSPackage che fornisce una finestra di progettazione.

Un'istanza della <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe viene utilizzata per modificare i metadati dei componenti creati in un'area di progettazione. Ad esempio, è possibile sostituire un visualizzatore proprietà predefinito utilizzato dagli <xref:System.Windows.Forms.CommonDialog> oggetti con un visualizzatore proprietà personalizzato.

Le modifiche fornite da un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> applicata all'implementazione di un VSPackage <xref:Microsoft.VisualStudio.Shell.Package> possono avere uno dei due ambiti seguenti:

- Globale: per tutte le nuove istanze di un determinato componente

- Local: si riferisce solo all'istanza del componente creato in un'area di progettazione fornita dal pacchetto VSPackage corrente.

La `IsGlobal` proprietà dell' <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> istanza di applicata all'implementazione di un VSPackage di <xref:Microsoft.VisualStudio.Shell.Package> determina questo ambito.

L'applicazione dell'attributo a un'implementazione di <xref:Microsoft.VisualStudio.Shell.Package> con la <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> proprietà dell' <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> oggetto impostato su `true` , come indicato di seguito, modifica il browser per l'intero ambiente di Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Se il flag globale è stato impostato su `false` , la modifica dei metadati è locale per la finestra di progettazione corrente supportata dal pacchetto VSPackage corrente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L'area di progettazione supporta solo la creazione di componenti e pertanto solo i componenti possono avere metadati locali. Nell'esempio precedente si stava tentando di modificare una proprietà, ad esempio la `Color` proprietà di un oggetto. Se `false` è stato passato per il flag globale, `CustomBrowser` non verrebbe mai visualizzato perché la finestra di progettazione non crea mai effettivamente un'istanza di `Color` . L'impostazione del flag globale su `false` è utile per i componenti di, ad esempio controlli, timer e finestre di dialogo.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Estendi supporto in fase di progettazione](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
