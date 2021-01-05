---
title: Incorporamento semplificato | Microsoft Docs
description: Informazioni sull'incorporamento semplificato, che può essere abilitato in un editor quando il relativo oggetto visualizzazione del documento è figlio di Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 99aaf5070646bbbb95c6be98eb8ac2f7a5948ff2
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715275"
---
# <a name="simplified-embedding"></a>Incorporamento semplificato
L'incorporamento semplificato viene abilitato in un editor quando il relativo oggetto visualizzazione del documento è associato a (ovvero è stato creato come figlio di) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia viene implementata per gestire i comandi della finestra. Gli editor di incorporamento semplificati non possono ospitare controlli attivi. Gli oggetti utilizzati per creare un editor con incorporamento semplificato sono illustrati nella figura seguente.

 ![Rappresentazione grafica dell'editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor con incorporamento semplificato

> [!NOTE]
> Negli oggetti di questa illustrazione, solo l' `CYourEditorFactory` oggetto è necessario per creare un editor standard basato su file. Se si crea un editor personalizzato, non è necessario implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> perché l'editor avrà probabilmente un proprio meccanismo di salvataggio permanente privato. Per gli editor non personalizzati, tuttavia, è necessario eseguire questa operazione.

 Tutte le interfacce implementate per creare un editor con incorporamento semplificato sono contenute nell' `CYourEditorDocument` oggetto. Tuttavia, per supportare più visualizzazioni dei dati del documento, suddividere le interfacce su dati separati e visualizzare gli oggetti come indicato nella tabella seguente.

|Interfaccia|Posizione dell'interfaccia|Usa|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizza|Fornisce la connessione alla finestra padre.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizza|Gestisce i comandi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizza|Consente gli aggiornamenti della barra di stato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizza|Abilita gli elementi della **casella degli strumenti** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Invia notifiche quando il file viene modificato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Abilita la funzionalità Salva con nome per un tipo di file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|Abilita il salvataggio permanente di un documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Consente l'eliminazione degli eventi di modifica del file, ad esempio l'attivazione del ricaricamento.|
