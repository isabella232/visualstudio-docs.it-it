---
title: Persistenza e tabella documenti in esecuzione | Microsoft Docs
description: Informazioni su come i progetti coordinano l'apertura, il salvataggio e la ridenominazione dei documenti nella tabella documenti in esecuzione, che tiene traccia dello stato del documento nell'IDE di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5244e14498da0f556a71b8d710ccbaa8b9b03e65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095121"
---
# <a name="persistence-and-the-running-document-table"></a>Salvataggio permanente e tabella documenti in esecuzione
Nell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, i progetti sono completamente responsabili della gestione della persistenza degli elementi del progetto, che eseguono usando il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . I documenti rappresentano l'unità di base di persistenza nell'ambiente Visual Studio. I progetti coordinano l'apertura, il salvataggio e la ridenominazione dei documenti con la tabella documenti in esecuzione (RDT), una risorsa che tiene traccia dello stato di tutti i documenti aperti.

## <a name="managing-persistence"></a>Gestione della persistenza
 I progetti controllano il servizio di persistenza dell'ambiente implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaccia. Sebbene l'ambiente non chieda mai direttamente a un documento di rendersi persistente, chiede al progetto (o alla gerarchia) proprietario di salvare il documento. In questo modo, il progetto può salvare i dati degli elementi del progetto in file locali, file remoti, database, repository o altro supporto.

 L'ambiente globale gestisce l'RDT. L'ambiente gestisce le voci per tutte le finestre e i documenti aperti in RDT, rendendo possibile la ricezione di notifiche speciali, ad esempio quando una soluzione viene chiusa. Inoltre, RDT consente all'ambiente di tenere traccia dei nodi corrispondenti in **Esplora soluzioni**. RDT gestisce un record per ogni oggetto aperto e permanente, inclusi i file di progetto e i documenti di elementi di progetto.

## <a name="see-also"></a>Vedi anche
- [Tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
