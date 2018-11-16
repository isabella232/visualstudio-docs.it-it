---
title: Incorporamento semplificato | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e59e09f475697ac0539384514837554e3ce85afc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736226"
---
# <a name="simplified-embedding"></a>Incorporamento semplificato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Incorporamento semplificato è abilitato in un editor, quando il relativo oggetto visualizzazione del documento è l'elemento figlio (vale a dire, resa figlio) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia viene implementata per gestire i comandi della finestra. Editor di incorporamento semplificato non può ospitare controlli attivi. Nella figura seguente vengono visualizzati gli oggetti utilizzati per creare un editor con incorporamento semplificato.  
  
 ![Rappresentazione grafica dell'Editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
Editor con incorporamento semplificato  
  
> [!NOTE]
>  Degli oggetti in questa illustrazione, solo il `CYourEditorFactory` oggetto è necessario per creare un editor basato su file standard. Se si sta creando un editor personalizzato, non occorre implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, poiché l'editor avrà probabilmente un proprio meccanismo di salvataggio permanente privato. Per gli editor non personalizzate, tuttavia, è necessario farlo.  
  
 Contenuti in tutte le interfacce implementate per creare un editor con incorporamento semplificato il `CYourEditorDocument` oggetto. Tuttavia, per supportare più visualizzazioni dei dati del documento, dividere le interfacce su oggetti di dati e visualizzazione separati, come indicato nella tabella seguente.  
  
|Interfaccia|Percorso dell'interfaccia|Usa|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizza|Fornisce una connessione alla finestra padre.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizza|Gestisce i comandi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizza|Consente gli aggiornamenti della barra di stato.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizza|Abilita **casella degli strumenti** elementi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dati|Invia notifiche quando il file modificato.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dati|Abilita la funzionalità Salva con nome per un tipo di file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dati|Abilita il salvataggio permanente di un documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dati|Consente di sopprimere gli eventi di modifica di file, dall'attivazione di ricaricamento di.|

