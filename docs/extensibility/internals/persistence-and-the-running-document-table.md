---
title: Persistenza e tabella documento in | Microsoft Docs
description: Informazioni sul modo in cui i progetti coordinano l'apertura, il salvataggio e la ridenominazione dei documenti nella tabella del documento in esecuzione, che tiene traccia dello stato del documento nell Visual Studio IDE.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1c4b37e5ae834a614cb741cb7589dad9dd1d6677
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709527"
---
# <a name="persistence-and-the-running-document-table"></a>Salvataggio permanente e tabella documenti in esecuzione
Nell'IDE, i progetti sono completamente responsabili della gestione della persistenza degli elementi di progetto, che vengono esersi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite il servizio , <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . I documenti sono l'unità di persistenza di base nell'Visual Studio locale. I progetti coordinano l'apertura, il salvataggio e la ridenominazione dei documenti con la tabella dei documenti in esecuzione, una risorsa che tiene traccia dello stato di tutti i documenti aperti.

## <a name="managing-persistence"></a>Gestione della persistenza
 I progetti controllano il servizio di persistenza dell'ambiente implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> l'interfaccia . Sebbene l'ambiente non chieda mai direttamente a un documento di rendere persistente se stesso, chiede al progetto (o alla gerarchia) proprietario di salvare il documento. Ciò consente al progetto di salvare i dati degli elementi di progetto in file locali, file remoti, un database, un repository o altro supporto.

 L'ambiente globale gestisce rdT. L'ambiente gestisce le voci per tutte le finestre aperte e i documenti in RDT, che consente loro di ricevere notifiche speciali, ad esempio quando una soluzione viene chiusa. RdT consente inoltre all'ambiente di tenere traccia dei nodi corrispondenti in **Esplora soluzioni**. RdT gestisce un record per ogni oggetto aperto e persistente, inclusi i file di progetto e i documenti degli elementi di progetto.

## <a name="see-also"></a>Vedi anche
- [Tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
