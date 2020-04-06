---
title: Incorporamento semplificato Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700078"
---
# <a name="simplified-embedding"></a>Incorporamento semplificato
L'incorporamento semplificato è abilitato in un editor quando il relativo oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]visualizzazione documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> è associato a (ovvero è stato creato come figlio di ) e l'interfaccia viene implementata per gestire i comandi della finestra. Gli editor di incorporamento semplificati non possono ospitare controlli attivi. Gli oggetti utilizzati per creare un editor con incorporamento semplificato sono illustrati nella figura seguente.

 ![Grafica dell'editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor con incorporamento semplificato

> [!NOTE]
> Tra gli oggetti in questa `CYourEditorFactory` illustrazione, solo l'oggetto è necessario per creare un editor standard basato su file. Se si crea un editor personalizzato, non <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>è necessario implementare , perché l'editor dirà probabilmente un proprio meccanismo di persistenza privata. Per gli editor non personalizzati, tuttavia, è necessario farlo.

 Tutte le interfacce implementate per creare un editor `CYourEditorDocument` con incorporamento semplificato sono contenute nell'oggetto. Tuttavia, per supportare più visualizzazioni dei dati del documento, suddividere le interfacce in oggetti di visualizzazione e dati separati, come indicato nella tabella seguente.

|Interfaccia|Posizione dell'interfaccia|Uso|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizza|Fornisce la connessione alla finestra padre.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizza|Gestisce i comandi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizza|Consente gli aggiornamenti della barra di stato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizza|Abilita gli elementi **della casella degli strumenti.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Invia notifiche quando il file cambia.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Attiva la funzione Salva con nome per un tipo di file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|Abilita il salvataggio permanente di un documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Consente la soppressione degli eventi di modifica dei file, ad esempio l'attivazione del ricaricamento.|
