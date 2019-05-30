---
title: Inizializzazione della finestra di progettazione e configurazione dei metadati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3084561be779eba73aa21ba7f23f7f5265bfd5b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348132"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Configurazione di inizializzazione e i metadati della finestra di progettazione

Modifica degli attributi dei metadati e il filtro associato a una finestra di progettazione o un componente della finestra di progettazione fornisce un meccanismo per le applicazioni definire quali strumenti vengono usati da una particolare finestra di progettazione per gestire diversi <xref:System.Type> oggetti (ad esempio strutture dei dati, le classi, o entità con interfaccia grafica), quando la finestra di progettazione è disponibile, e come IDE di Visual Studio è configurato per supportare la finestra di progettazione (per istanza quali **casella degli strumenti** categoria o scheda è disponibile).

Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] offre diversi meccanismi per facilitare il controllo dell'inizializzazione di una finestra di progettazione o del componente della finestra di progettazione e la manipolazione dei relativi metadati da un pacchetto VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inizializzare le informazioni dei metadati e configurazione
 Poiché vengono caricati su richiesta, è possano i pacchetti VSPackage non siano stati caricati dall'ambiente di Visual Studio prima della creazione di istanze di una finestra di progettazione. Di conseguenza, i pacchetti VSPackage non è possibile usare il meccanismo standard per la configurazione di un componente della finestra di progettazione o progettazione al momento della creazione, che consiste nel gestire un <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> evento. Al contrario, un pacchetto VSPackage implementa un'istanza del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> l'interfaccia e si registra per fornire le personalizzazioni, detti estensioni della superficie di progettazione.

### <a name="customize-initialization"></a>Personalizzare l'inizializzazione

Personalizzazione di una finestra di progettazione, un componente o un'area di progettazione, include:

1. Modifica i metadati della finestra di progettazione e la modifica in modo efficace la modalità di una determinata <xref:System.Type> sono accessibili o convertiti.

    Questa operazione viene in genere eseguita tramite il <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.TypeConverter> meccanismi.

    Ad esempio, quando <xref:System.Windows.Forms>-vengono inizializzate basata su finestre di progettazione, l'ambiente di Visual Studio modifica il <xref:System.Drawing.Design.UITypeEditor> per <xref:System.Web.UI.WebControls.Image> oggetti utilizzati con la finestra di progettazione per utilizzare il gestore di risorse per ottenere le bitmap anziché nel file system.

2. L'integrazione con l'ambiente, ad esempio, la sottoscrizione di eventi o per ottenere le informazioni di configurazione di progetto. È possibile ottenere informazioni sulla configurazione di progetto e sottoscrivere eventi ottenendo il <xref:System.ComponentModel.Design.ITypeResolutionService> interfaccia.

3. Modifica dell'ambiente utente attivando appropriato **casella degli strumenti** categorie o limitando l'applicabilità della finestra di progettazione tramite l'applicazione di un'istanza del <xref:System.ComponentModel.ToolboxItemFilterAttribute> classe nella finestra di progettazione.

### <a name="designer-initialization-by-a-vspackage"></a>Inizializzazione della finestra di progettazione da un pacchetto VSPackage

Un pacchetto VSPackage deve gestire l'inizializzazione della finestra di progettazione da:

1. Creazione di un oggetto che implementa il <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe.

   > [!NOTE]
   > Il <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> classe non deve essere implementata mai sullo stesso oggetto come il <xref:Microsoft.VisualStudio.Shell.Package> classe.

2. La registrazione della classe che implementa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> come fornire supporto per le estensioni della finestra di progettazione del pacchetto VSPackage. Registrare la classe applicando le istanze di <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>, e <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> alla classe che fornisce l'implementazione di VSPackage del <xref:Microsoft.VisualStudio.Shell.Package>.

Ogni volta che viene creata una finestra di progettazione o un componente della finestra di progettazione, l'ambiente di Visual Studio:

- Accede a ogni provider di estensione dell'area di progettazione registrato.

- Crea e inizializza un'istanza di ciascun provider di estensione dell'area di progettazione <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oggetto.

- Ogni provider di estensione dell'area di progettazione chiama <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> metodo o <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> metodo (se necessario).

Quando si implementa il <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> dell'oggetto come membro di un pacchetto VSPackage, è importante comprendere che:

- Ambiente di Visual Studio non fornisce alcun controllo su quali metadati o altre impostazioni di configurazione particolari `DesignSurfaceExtension` modifica del provider. È possibile che due o più `DesignSurfaceExtension` provider modifica la stessa funzionalità della finestra di progettazione in molti modi in conflitto con la modifica finale in definitiva. È indeterminato quale modifica viene applicata ultima.

- È possibile limitare in modo esplicito un'implementazione del <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> oggetti nelle finestre di progettazione specifico applicando le istanze di <xref:System.ComponentModel.ToolboxItemFilterAttribute> al tipo di implementazione. Per ulteriori informazioni sul **casella degli strumenti** elemento filtro, vedere la <xref:System.ComponentModel.ToolboxItemFilterAttribute> e <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>Il provisioning di metadati aggiuntivi

Un pacchetto VSPackage può modificare la configurazione di una finestra di progettazione o un componente della finestra di progettazione diverso da in fase di progettazione.

Il <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe può essere utilizzata a livello di codice o applicata a un pacchetto VSPackage che fornisce una finestra di progettazione.

Un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> classe viene utilizzata per modificare i metadati di componenti creati in un'area di progettazione. Ad esempio, uno è stato possibile sostituire un visualizzatore di proprietà predefinito usato da <xref:System.Windows.Forms.CommonDialog> oggetti con un visualizzatore proprietà personalizzato.

Modifiche fornite da un'istanza di <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> applicato a un'implementazione di VSPackage <xref:Microsoft.VisualStudio.Shell.Package> può avere uno dei due ambiti:

- Globale, per tutte le nuove istanze di un dato componente

- Locale, si riferisce solo all'istanza del componente creato in un'area di progettazione fornita da VSPackage corrente.

Il `IsGlobal` proprietà del <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> applicato a un'implementazione di VSPackage istanza <xref:Microsoft.VisualStudio.Shell.Package> determina l'ambito.

Applicando l'attributo a un'implementazione di <xref:Microsoft.VisualStudio.Shell.Package> con il <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> proprietà delle <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> oggetto impostato su `true`, come indicato di seguito, viene modificato il browser per l'intero ambiente di Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Se il flag globale è stato impostato su `false`, quindi la modifica dei metadati è locale rispetto alla finestra di progettazione corrente è supportata dal pacchetto VSPackage corrente:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> L'area di progettazione supporta solo la creazione di componenti e pertanto solo i componenti possono avere metadati locali. Nell'esempio precedente, abbiamo stavamo tenta di modificare una proprietà, ad esempio il `Color` proprietà di un oggetto. Se `false` passato per il flag globale `CustomBrowser` mai vengono visualizzati perché la finestra di progettazione crea mai un'istanza di `Color`. Impostazione del flag globale su `false` è utile per i componenti, ad esempio controlli, timer e le finestre di dialogo.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Estendere il supporto in fase di progettazione](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)