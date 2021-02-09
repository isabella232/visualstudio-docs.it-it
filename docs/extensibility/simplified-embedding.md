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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f62e3a4f33193f36e76b1286ae3d35d26706b3ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928094"
---
# <a name="simplified-embedding"></a>Incorporamento semplificato
L'incorporamento semplificato viene abilitato in un editor quando il relativo oggetto visualizzazione del documento è associato a (ovvero è stato creato come figlio di) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia viene implementata per gestire i comandi della finestra. Gli editor di incorporamento semplificati non possono ospitare controlli attivi. Gli oggetti utilizzati per creare un editor con incorporamento semplificato sono illustrati nella figura seguente.

 ![Rappresentazione grafica dell'editor di incorporamento semplificato](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor con incorporamento semplificato

> [!NOTE]
> Negli oggetti di questa illustrazione, solo l' `CYourEditorFactory` oggetto è necessario per creare un editor standard basato su file. Se si crea un editor personalizzato, non è necessario implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> perché l'editor avrà probabilmente un proprio meccanismo di salvataggio permanente privato. Per gli editor non personalizzati, tuttavia, è necessario eseguire questa operazione.

 Tutte le interfacce implementate per creare un editor con incorporamento semplificato sono contenute nell' `CYourEditorDocument` oggetto. Tuttavia, per supportare più visualizzazioni dei dati del documento, suddividere le interfacce su dati separati e visualizzare gli oggetti come indicato nella tabella seguente.

|Interfaccia|Posizione dell'interfaccia|Uso|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Visualizzazione|Fornisce la connessione alla finestra padre.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Visualizzazione|Gestisce i comandi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizzazione|Consente gli aggiornamenti della barra di stato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizzazione|Abilita gli elementi della **casella degli strumenti** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Data|Invia notifiche quando il file viene modificato.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Data|Abilita la funzionalità Salva con nome per un tipo di file.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Data|Abilita il salvataggio permanente di un documento.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Data|Consente l'eliminazione degli eventi di modifica del file, ad esempio l'attivazione del ricaricamento.|
