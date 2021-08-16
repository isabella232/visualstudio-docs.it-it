---
title: Incorporamento semplificato | Microsoft Docs
description: Informazioni sull'incorporamento semplificato, che può essere abilitato in un editor quando il relativo oggetto visualizzazione documento è figlio di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ea5186872232f3c84ac41567938ea5822915746b37adafffe7263077d3c87b43
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121260371"
---
# <a name="simplified-embedding"></a>Incorporamento semplificato
L'incorporamento semplificato è abilitato in un editor quando il relativo oggetto visualizzazione documento è associato a (ovvero è reso figlio di) e l'interfaccia viene implementata per gestire i relativi comandi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> della finestra. Gli editor di incorporamento semplificati non possono ospitare controlli attivi. Gli oggetti utilizzati per creare un editor con incorporamento semplificato sono illustrati nella figura seguente.

 ![Immagine dell'editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor con incorporamento semplificato

> [!NOTE]
> Tra gli oggetti in questa illustrazione, solo `CYourEditorFactory` l'oggetto è necessario per creare un editor standard basato su file. Se si crea un editor personalizzato, non è necessario implementare , perché è probabile che l'editor abbia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> un proprio meccanismo di persistenza privato. Per gli editor non personalizzati, tuttavia, è necessario farlo.

 Tutte le interfacce implementate per creare un editor con incorporamento semplificato sono contenute `CYourEditorDocument` nell'oggetto . Tuttavia, per supportare più visualizzazioni dei dati del documento, suddividere le interfacce in oggetti dati e oggetti visualizzazione separati, come indicato nella tabella seguente.

|Interfaccia|Posizione dell'interfaccia|Uso|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizzazione|Fornisce la connessione alla finestra padre.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizzazione|Gestisce i comandi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizzazione|Consente gli aggiornamenti della barra di stato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizzazione|Abilita gli **elementi della casella** degli strumenti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dati|Invia notifiche quando il file viene modificato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dati|Abilita la funzionalità Salva con nome per un tipo di file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Dati|Abilita il salvataggio permanente di un documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dati|Consente l'eliminazione degli eventi di modifica dei file, ad esempio l'attivazione del ricaricamento.|
