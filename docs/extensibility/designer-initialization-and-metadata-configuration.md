---
title: Inizializzazione della finestra di progettazione e configurazione dei metadati | Microsoft Docs
description: Informazioni su come Visual Studio SDK semplifica il controllo dell'inizializzazione di una finestra di progettazione o di un componente della finestra di progettazione e dei relativi metadati da parte di un PACCHETTO VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 617ee2f4a43cb10e5db51577d0f3892952971369929e91bf293ab0506874a7f3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377002"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inizializzazione della finestra di progettazione e configurazione dei metadati

La modifica dei metadati e degli attributi di filtro associati a una finestra di progettazione o a un componente della finestra di progettazione fornisce un meccanismo che consente alle applicazioni di definire quali strumenti vengono usati da una finestra di progettazione specifica per gestire oggetti diversi ,ad esempio strutture di dati, classi o entità grafiche, quando la finestra di progettazione è disponibile e come l'IDE di Visual Studio è configurato per supportare la finestra di progettazione, ad esempio la categoria o la scheda della casella degli strumenti <xref:System.Type> disponibile. 

fornisce diversi meccanismi per facilitare il controllo dell'inizializzazione di una finestra di progettazione o di un componente della finestra di progettazione e la manipolazione dei relativi metadati [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] da parte di un PACCHETTO VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inizializzare metadati e informazioni di configurazione
 Poiché vengono caricati su richiesta, i pacchetti VSPackage potrebbero non essere stati caricati dall'ambiente Visual Studio prima della creazione di un'istanza di una finestra di progettazione. Di conseguenza, i pacchetti VSPackage non possono usare il meccanismo standard per configurare una finestra di progettazione o un componente della finestra di progettazione al momento della creazione, ovvero per gestire un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> evento. Un VSPackage implementa invece un'istanza dell'interfaccia e si registra per fornire personalizzazioni, definite <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> estensioni dell'area di progettazione.

### <a name="customize-initialization"></a>Personalizzare l'inizializzazione

La personalizzazione di una finestra di progettazione, di un componente o di un'area di progettazione comporta:

1. Modifica dei metadati della finestra di progettazione e modifica efficace della modalità di accesso o conversione <xref:System.Type> di un determinato oggetto .

    Questa operazione viene in genere eseguita <xref:System.Drawing.Design.UITypeEditor> tramite i meccanismi o <xref:System.ComponentModel.TypeConverter> .

    Ad esempio, quando le finestre di progettazione basate su vengono inizializzate, l'ambiente Visual Studio modifica l'oggetto per gli oggetti utilizzati con la finestra di progettazione in modo da usare gestione risorse per ottenere bitmap anziché <xref:System.Windows.Forms> <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> file system.

2. L'integrazione con l'ambiente, ad esempio, tramite la sottoscrizione di eventi o l'acquisizione di informazioni di configurazione del progetto. È possibile ottenere informazioni sulla configurazione del progetto e sottoscrivere gli eventi ottenendo <xref:System.ComponentModel.Design.ITypeResolutionService> l'interfaccia .

3. Modifica dell'ambiente utente attivando le categorie appropriate della casella degli strumenti o limitando l'applicabilità della finestra di progettazione applicando un'istanza della classe alla finestra di  <xref:System.ComponentModel.ToolboxItemFilterAttribute> progettazione.

### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da parte di un pacchetto VSPackage

Un PACCHETTO VSPackage deve gestire l'inizializzazione della finestra di progettazione tramite:

1. Creazione di un oggetto che implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe .

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe non deve mai essere implementata nello stesso oggetto della classe <xref:Microsoft.VisualStudio.Shell.Package> .

2. Registrazione della classe che implementa come supporto per le estensioni della finestra di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> progettazione del VSPackage. Registrare la classe applicando istanze di , e alla classe che  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> fornisce <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> l'implementazione del VSPackage di <xref:Microsoft.VisualStudio.Shell.Package> .

Ogni volta che viene creata una finestra di progettazione o un componente della finestra di progettazione, Visual Studio ambiente:

- Accede a ogni provider di estensioni dell'area di progettazione registrato.

- Crea un'istanza di e inizializza un'istanza dell'oggetto di ogni provider dell'estensione dell'area di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> progettazione.

- Chiama il metodo o il metodo di ogni provider di estensione dell'area di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> progettazione (in base alle esigenze).

Quando si implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> l'oggetto come membro di un VSPackage, è importante comprendere che:

- L Visual Studio ambiente non fornisce alcun controllo sui metadati o su altre impostazioni di configurazione che `DesignSurfaceExtension` un determinato provider modifica. È possibile per due o più provider modificare la stessa funzionalità della finestra di progettazione in modo in conflitto, con `DesignSurfaceExtension` la modifica finale definitiva. L'ultima modifica applicata è indeterminata.

- È possibile limitare in modo esplicito un'implementazione dell'oggetto a finestre di progettazione specifiche <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> applicando istanze di a tale <xref:System.ComponentModel.ToolboxItemFilterAttribute> implementazione. Per altre informazioni sul filtro **degli elementi** della casella degli strumenti, vedere <xref:System.ComponentModel.ToolboxItemFilterAttribute> e <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Provisioning aggiuntivo dei metadati

Un VSPackage può modificare la configurazione di una finestra di progettazione o di un componente della finestra di progettazione diverso da in fase di progettazione.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe può essere usata a livello di codice o applicata a un VSPackage che fornisce una finestra di progettazione.

Un'istanza della <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe viene utilizzata per modificare i metadati dei componenti creati in un'area di progettazione. Ad esempio, è possibile sostituire un visualizzatore proprietà predefinito usato dagli <xref:System.Windows.Forms.CommonDialog> oggetti con un visualizzatore proprietà personalizzato.

Le modifiche fornite da un'istanza di applicata all'implementazione di un VSPackage di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> possono avere uno dei due ambiti <xref:Microsoft.VisualStudio.Shell.Package> seguenti:

- Globale: per tutte le nuove istanze di un determinato componente

- Local: riguarda solo l'istanza del componente creato in un'area di progettazione fornita dal VSPackage corrente.

La `IsGlobal` proprietà <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> dell'istanza applicata all'implementazione di un VSPackage di <xref:Microsoft.VisualStudio.Shell.Package> determina questo ambito.

L'applicazione dell'attributo a un'implementazione di con la proprietà dell'oggetto impostata su , come illustrato di seguito, modifica il browser per <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> l'intero Visual Studio `true` ambiente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Se il flag globale è stato impostato su , la modifica dei metadati è locale rispetto alla finestra di progettazione `false` corrente supportata dal pacchetto VSPackage corrente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L'area di progettazione supporta solo la creazione di componenti e pertanto solo i componenti possono avere metadati locali. Nell'esempio precedente si è tentato di modificare una proprietà, ad esempio la `Color` proprietà di un oggetto . Se è stato passato per il flag globale, non viene mai visualizzato perché la finestra di progettazione non crea mai effettivamente `false` `CustomBrowser` un'istanza di `Color` . L'impostazione del flag globale `false` su è utile per i componenti, ad esempio controlli, timer e finestre di dialogo.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Estendere il supporto in fase di progettazione](/previous-versions/37899azc(v=vs.140))