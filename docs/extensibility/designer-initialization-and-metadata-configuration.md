---
title: 'Inizializzazione della finestra di progettazione e configurazione dei metadati : Documenti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712219"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inizializzazione della finestra di progettazione e configurazione dei metadati

La modifica dei metadati e degli attributi di filtro associati a una finestra di progettazione <xref:System.Type> o a un componente della finestra di progettazione fornisce un meccanismo per le applicazioni per definire gli strumenti utilizzati da una determinata finestra di progettazione per gestire oggetti diversi (ad esempio strutture di dati, classi o entità grafiche), quando la finestra di progettazione è disponibile e come l'IDE di Visual Studio è configurato per supportare la finestra di progettazione (ad esempio quale categoria o scheda **della casella degli strumenti** è disponibile).

Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce diversi meccanismi per facilitare il controllo dell'inizializzazione di una finestra di progettazione o di un componente della finestra di progettazione e la modifica dei relativi metadati da un VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inizializzare i metadati e le informazioni di configurazione
 Poiché vengono caricati su richiesta, VSPackage potrebbero non essere stati caricati dall'ambiente di Visual Studio prima della creazione di un'istanza di una finestra di progettazione. Pertanto, VSPackage non è possibile utilizzare il meccanismo standard per la <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> configurazione di una finestra di progettazione o di un componente della finestra di progettazione durante la creazione, ovvero gestire un evento. Al contrario, un VSPackage <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementa un'istanza dell'interfaccia e si registra per fornire personalizzazioni, denominate estensioni dell'area di progettazione.

### <a name="customize-initialization"></a>Personalizzare l'inizializzazione

La personalizzazione di una finestra di progettazione, di un componente o di un'area di progettazione comporta:Customizing a designer, a component, or a designer surface, involves:

1. Modifica dei metadati della finestra <xref:System.Type> di progettazione e modifica efficace della modalità di accesso o conversione di determinati elementi.

    Questa operazione viene <xref:System.Drawing.Design.UITypeEditor> in <xref:System.ComponentModel.TypeConverter> genere eseguita tramite i meccanismi o .

    Ad esempio, <xref:System.Windows.Forms>quando vengono inizializzate le finestre di progettazione <xref:System.Drawing.Design.UITypeEditor> basate <xref:System.Web.UI.WebControls.Image> su Visual Studio, l'ambiente di Visual Studio modifica gli oggetti for utilizzati con la finestra di progettazione per utilizzare il gestore di risorse per ottenere bitmap anziché il file system.

2. Integrazione con l'ambiente, ad esempio, sottoscrivendo eventi o ottenendo informazioni sulla configurazione del progetto. È possibile ottenere informazioni sulla configurazione del <xref:System.ComponentModel.Design.ITypeResolutionService> progetto e sottoscrivere eventi ottenendo l'interfaccia.

3. Modifica dell'ambiente utente attivando le categorie **della casella degli strumenti** appropriate o limitando l'applicabilità della finestra di progettazione applicando un'istanza <xref:System.ComponentModel.ToolboxItemFilterAttribute> della classe alla finestra di progettazione.

### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da un VSPackage

Un pacchetto VSPackage deve gestire l'inizializzazione della finestra di progettazione da:A VSPackage should handle designer initialization by:

1. Creazione di un <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oggetto che implementa la classe.

   > [!NOTE]
   > La <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe non deve mai essere <xref:Microsoft.VisualStudio.Shell.Package> implementata sullo stesso oggetto della classe.

2. Registrazione della classe <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> che implementa come fornire il supporto per le estensioni della finestra di progettazione del pacchetto VSPackage.Registering the class that implements as providing support for the VSPackage's designer extensions. Registrare la classe applicando <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>istanze <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> di , e alla classe che <xref:Microsoft.VisualStudio.Shell.Package>fornisce l'implementazione di .

Ogni volta che viene creata una finestra di progettazione o un componente della finestra di progettazione, l'ambiente di Visual Studio:Whenever a designer or designer component is created, the Visual Studio environment:

- Accede a ogni provider di estensione dell'area di progettazione registrato.

- Crea un'istanza e inizializza un'istanza dell'oggetto di ogni provider di estensione dell'area <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> di progettazione.

- Chiama il metodo o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> il metodo di ogni provider di estensione dell'area di progettazione (se appropriato).

Quando si <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementa l'oggetto come membro di un VSPackage, è importante comprendere che:When implementing the object as a member of a VSPackage, it is important to understand that:

- L'ambiente di Visual Studio non fornisce alcun controllo `DesignSurfaceExtension` sui metadati o altre impostazioni di configurazione di un determinato provider. È possibile che due `DesignSurfaceExtension` o più provider modifichino la stessa funzionalità di progettazione in modo in conflitto, con la modifica finale definitiva. È indeterminato quale modifica viene applicata per ultima.

- È possibile limitare in modo <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> esplicito un'implementazione dell'oggetto a finestre di progettazione specifiche applicando istanze di <xref:System.ComponentModel.ToolboxItemFilterAttribute> a tale implementazione. Per ulteriori informazioni sul filtro <xref:System.ComponentModel.ToolboxItemFilterAttribute> degli <xref:System.ComponentModel.ToolboxItemFilterType>elementi della casella **degli strumenti,** vedere e .

## <a name="additional-metadata-provisioning"></a>Provisioning di metadati aggiuntivi

Un pacchetto VSPackage può modificare la configurazione di una finestra di progettazione o di un componente della finestra di progettazione diverso in fase di progettazione.

La <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe può essere utilizzata a livello di codice o applicata a un pacchetto VSPackage che fornisce una finestra di progettazione.

Un'istanza <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> della classe viene utilizzata per modificare i metadati dei componenti creati in un'area di progettazione. Ad esempio, è possibile sostituire un <xref:System.Windows.Forms.CommonDialog> visualizzatore proprietà predefinito utilizzato dagli oggetti con un visualizzatore proprietà personalizzato.

Le modifiche fornite da <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> un'istanza di applicata <xref:Microsoft.VisualStudio.Shell.Package> all'implementazione di un VSPackage possono avere uno dei due ambiti:Modifications provided by an instance of applied to a VSPackage's implementation of can have one of two scopes:

- Globale -- per tutte le nuove istanze di un determinato componente

- Locale -- riguarda solo l'istanza del componente creato in un'area di progettazione fornita dal pacchetto VSPackage corrente.

La `IsGlobal` proprietà <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> dell'istanza applicata all'implementazione di <xref:Microsoft.VisualStudio.Shell.Package> un VSPackage determina questo ambito.

L'applicazione dell'attributo <xref:Microsoft.VisualStudio.Shell.Package> a <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> un'implementazione di con la proprietà dell'oggetto <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> impostata su `true`, come indicato di seguito, modifica il browser per l'intero ambiente Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Se il flag globale `false`è stato impostato su , la modifica dei metadati è locale rispetto alla finestra di progettazione corrente supportata dal pacchetto VSPackage corrente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L'area di progettazione supporta solo la creazione di componenti e pertanto solo i componenti possono avere metadati locali. Nell'esempio precedente, stavamo tentando di modificare una `Color` proprietà, ad esempio la proprietà di un oggetto. Se `false` è stato passato per `CustomBrowser` il flag globale, non verrà `Color`mai visualizzato perché la finestra di progettazione non crea mai effettivamente un'istanza di . L'impostazione `false` del flag globale su è utile per i componenti, ad esempio controlli, timer e finestre di dialogo.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Estendere il supporto in fase di progettazioneExtend design-time support](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
