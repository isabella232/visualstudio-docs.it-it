---
title: Inizializzazione della finestra di progettazione e configurazione dei metadati | Microsoft Docs
description: Informazioni su come Visual Studio SDK facilita il controllo dell'inizializzazione di una finestra di progettazione o di un componente della finestra di progettazione e dei relativi metadati da parte di un VSPackage.
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
ms.openlocfilehash: 2954d551b1a35c2de5e951111e746227aa9987a5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159542"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inizializzazione della finestra di progettazione e configurazione dei metadati

La manipolazione dei metadati e degli attributi di filtro associati a una finestra di progettazione o a un componente della finestra di progettazione fornisce un meccanismo per le applicazioni per definire quali strumenti vengono usati da una determinata finestra di progettazione per gestire oggetti diversi (ad esempio strutture di dati, classi o entità grafiche), quando la finestra di progettazione è disponibile e come l'IDE di Visual Studio è configurato per supportare la finestra di progettazione ,ad esempio la categoria o la scheda della casella degli strumenti <xref:System.Type> disponibile. 

Fornisce diversi meccanismi per facilitare il controllo dell'inizializzazione di una finestra di progettazione o di un componente di progettazione e la manipolazione dei relativi metadati da parte di [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inizializzare metadati e informazioni di configurazione
 Poiché vengono caricati su richiesta, i pacchetti VSPackage potrebbero non essere stati caricati dall'ambiente Visual Studio prima della creazione di un'istanza di una finestra di progettazione. Pertanto, i pacchetti VSPackage non possono usare il meccanismo standard per la configurazione di una finestra di progettazione o di un componente della finestra di progettazione al momento della creazione, ovvero per gestire un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> evento. Un vspackage implementa invece un'istanza dell'interfaccia e si registra per fornire personalizzazioni, definite <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> estensioni dell'area di progettazione.

### <a name="customize-initialization"></a>Personalizzare l'inizializzazione

La personalizzazione di una finestra di progettazione, di un componente o di un'area di progettazione comporta:

1. Modifica dei metadati della finestra di progettazione e modifica efficace della modalità di accesso o <xref:System.Type> conversione di un determinato oggetto .

    Questa operazione viene in genere eseguita tramite <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> i meccanismi o .

    Ad esempio, quando le finestre di progettazione basate su vengono inizializzate, l'ambiente Visual Studio modifica l'oggetto per gli oggetti usati con la finestra di progettazione in modo da usare gestione risorse per ottenere <xref:System.Windows.Forms> bitmap anziché l'file system. <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image>

2. Integrazione con l'ambiente, ad esempio, sottoscrivendo eventi o ottenendo informazioni di configurazione del progetto. È possibile ottenere informazioni di configurazione del progetto e sottoscrivere gli eventi ottenendo <xref:System.ComponentModel.Design.ITypeResolutionService> l'interfaccia .

3. Modifica dell'ambiente utente attivando le **categorie** appropriate della casella degli strumenti o limitando l'applicabilità della finestra di progettazione applicando un'istanza della classe <xref:System.ComponentModel.ToolboxItemFilterAttribute> alla finestra di progettazione.

### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da parte di un vspackage

Un VSPackage deve gestire l'inizializzazione della finestra di progettazione tramite:

1. Creazione di un oggetto che implementa la <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe .

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe non deve mai essere implementata nello stesso oggetto della classe <xref:Microsoft.VisualStudio.Shell.Package> .

2. Registrazione della classe che implementa come supporto per le estensioni della finestra di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> del pacchetto VSPackage. Registrare la classe applicando istanze di , e alla classe che fornisce  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> l'implementazione di VSPackage di <xref:Microsoft.VisualStudio.Shell.Package> .

Ogni volta che viene creata una finestra di progettazione o un componente della finestra di progettazione, l'Visual Studio seguente:

- Accede a ogni provider di estensioni dell'area di progettazione registrato.

- Crea un'istanza e inizializza un'istanza di ogni oggetto del provider di estensioni dell'area di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> progettazione.

- Chiama il metodo o il metodo di ogni provider di estensioni dell'area di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> progettazione (in base alle esigenze).

Quando si implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> l'oggetto come membro di un pacchetto VSPackage, è importante comprendere che:

- L Visual Studio ambiente non fornisce alcun controllo sui metadati o altre impostazioni di configurazione che un `DesignSurfaceExtension` determinato provider modifica. È possibile per due o più provider modificare la stessa funzionalità della finestra di progettazione in modo in conflitto, con `DesignSurfaceExtension` la modifica finale definitiva. L'ultima modifica applicata è indeterminata.

- È possibile limitare in modo esplicito un'implementazione dell'oggetto a finestre di progettazione specifiche applicando <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> istanze di a tale <xref:System.ComponentModel.ToolboxItemFilterAttribute> implementazione. Per altre informazioni sul filtro **degli elementi** della casella degli strumenti, vedere <xref:System.ComponentModel.ToolboxItemFilterAttribute> e <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Provisioning aggiuntivo dei metadati

Un VSPackage può modificare la configurazione di una finestra di progettazione o di un componente della finestra di progettazione diverso da in fase di progettazione.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe può essere utilizzata a livello di codice o applicata a un VSPackage che fornisce una finestra di progettazione.

Un'istanza della <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe viene utilizzata per modificare i metadati dei componenti creati in un'area di progettazione. Ad esempio, è possibile sostituire un visualizzatore proprietà predefinito usato dagli <xref:System.Windows.Forms.CommonDialog> oggetti con un Visualizzatore proprietà personalizzato.

Le modifiche fornite da un'istanza di applicata all'implementazione di un <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> VSPackage di possono avere uno dei due <xref:Microsoft.VisualStudio.Shell.Package> ambiti seguenti:

- Globale: per tutte le nuove istanze di un determinato componente

- Local: relativo solo all'istanza del componente creato in un'area di progettazione fornita dal vspackage corrente.

La `IsGlobal` proprietà <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> dell'istanza applicata all'implementazione di un VSPackage di <xref:Microsoft.VisualStudio.Shell.Package> determina questo ambito.

L'applicazione dell'attributo a <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> un'implementazione di con la proprietà dell'oggetto impostata su , come indicato di seguito, modifica il browser per `true` l'intero Visual Studio ambiente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Se il flag globale è stato impostato su , la modifica dei metadati è locale rispetto alla finestra di progettazione corrente `false` supportata dal pacchetto VSPackage corrente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L'area di progettazione supporta solo la creazione di componenti e pertanto solo i componenti possono avere metadati locali. Nell'esempio precedente si è tentato di modificare una proprietà, ad esempio `Color` la proprietà di un oggetto . Se fosse stato passato per il flag globale, non verrebbe mai visualizzato perché la finestra di progettazione non `false` `CustomBrowser` crea mai effettivamente un'istanza di `Color` . L'impostazione del flag globale su è utile per i componenti, ad `false` esempio controlli, timer e finestre di dialogo.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Estendere il supporto in fase di progettazione](/previous-versions/37899azc(v=vs.140))