---
title: La gestione della casella degli strumenti | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: fa9b30429de00f950e4d9de160fe72ece7f06760
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517350"
---
# <a name="managing-the-toolbox"></a>Managing the Toolbox
Il [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] consente a un VSPackage, ad esempio un editor o finestra di progettazione per gestire l'appartenenza e l'aspetto del **casella degli strumenti**.  
  
 La **casella degli strumenti** può inoltre essere gestita usando l'automazione. Per altre informazioni sulla gestione di una casella degli strumenti tramite l'automazione, vedere [procedura: Control the Toolbox](http://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Selezione automatica della scheda della casella degli strumenti  
 Una scheda o una categoria specifica della **casella degli strumenti** può essere impostata automaticamente come attiva in base alla finestra di progettazione o all'editor attualmente attivo. Ad esempio, se è attivata una finestra di progettazione di form, si potrebbe voler impostare come attiva la scheda **Tutti i Windows Form** .  
  
 Questo supporto è limitato a editor e finestre di progettazione che richiedono:  
  
1.  L'implementazione di un oggetto factory per fornire istanze dell'editor o della finestra di progettazione. Per altre informazioni sull'implementazione di un oggetto factory dell'editor o finestra di progettazione, vedere [factory dell'Editor](../extensibility/editor-factories.md).  
  
2.  La registrazione della scheda della casella degli strumenti che è attivata automaticamente se è presente l'editor o la finestra di progettazione.  
  
## <a name="controlling-the-toolbox"></a>Controllo della casella degli strumenti  
 Integrando il supporto per automazione, il [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fornisce le interfacce seguenti per offrire i pacchetti VSPackage un maggiore controllo sulla gestione della **casella degli strumenti** è gestito.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Consente alle applicazioni di gestire, aggiungere e rimuovere <xref:System.Drawing.Design.ToolboxItem> oggetti dal **casella degli strumenti**. Consente inoltre di configurare l'aspetto e le categorie della **casella degli strumenti** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Consente alle applicazioni di gestire, aggiungere e rimuovere controlli della **casella degli strumenti** basati su ActiveX, nonché di configurare le categorie e l'aspetto della **casella degli strumenti** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Estende le funzionalità disponibili in <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> fornendo supporto completo per il salvataggio permanente e la localizzazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Ci sono diversi aspetti importanti da tenere presenti quando si usano queste interfacce:  
  
-   <xref:System.Drawing.Design.IToolboxService> è disponibile solo per pacchetti VSPackage basati sul framework di pacchetto gestito (MPF, Managed Package Framework).  
  
-   Controlli non possono essere aggiunti direttamente per la **casella degli strumenti** usando <xref:System.Drawing.Design.IToolboxService>.  
  
-   Un pacchetto VSPackage deve usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> per aggiungere controlli oppure ospitare il controllo in un controllo wrapper che deriva da <xref:System.Windows.Forms.AxHost>.  
  
     Visual Studio fornisce lo strumento `Aximp.exe` per l'automazione del wrapping di un controllo ActiveX in un controllo derivato da <xref:System.Windows.Forms.AxHost>. Per altre informazioni, vedere [Aximp.exe (Windows Form Control Importer di ActiveX)](http://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> sono interfacce basate su COM disponibili tramite gli assembly di interoperabilità.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> deriva da <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> e implementa tutti i relativi metodi.  
  
     Gli oggetti ottengono solo un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> non deriva da <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e non implementa i relativi metodi.  
  
     Gli oggetti che richiedono funzionalità in entrambe le interfacce devono ottenere le istanze di entrambe le interfacce dall'ambiente.  
  
-   Quando si usano <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>, le informazioni sui nomi canonici (non localizzati) delle schede vengono gestite dai metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A>.  
  
-   Quando si usa <xref:System.Drawing.Design.IToolboxService>, è responsabilità di chi esegue l'implementazione gestire le informazioni localizzate, ad esempio i nomi delle categorie.  
  
 Usare il meccanismo delle impostazioni per consentire agli utenti di salvare le impostazioni della **casella degli strumenti** a cui gli utenti accedono dal comando **Importa/Esporta impostazioni** , disponibile nel menu **Strumenti** dell'IDE. Per altre informazioni su come usare le impostazioni, vedere [Extending User Settings and Options](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione della casella degli strumenti](../misc/extending-the-toolbox.md)