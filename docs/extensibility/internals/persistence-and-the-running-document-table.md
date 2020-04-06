---
title: Persistenza e la tabella del documento in esecuzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706725"
---
# <a name="persistence-and-the-running-document-table"></a>Salvataggio permanente e tabella documenti in esecuzione
Nell'IDE, i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetti sono completamente responsabili della gestione della persistenza <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>dei relativi elementi di progetto, che vengono eseguiti utilizzando il servizio, . I documenti sono l'unità di base di persistenza nell'ambiente di Visual Studio.Documents are the basic unit of persistence in the Visual Studio environment. I progetti coordinano l'apertura, il salvataggio e la ridenominazione dei documenti con la tabella documenti in esecuzione (RDT), una risorsa che tiene traccia dello stato di tutti i documenti aperti.

## <a name="managing-persistence"></a>Gestione della persistenzaManaging Persistence
 I progetti controllano il servizio <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> di persistenza dell'ambiente implementando l'interfaccia. Mentre l'ambiente non chiede mai direttamente a un documento di persistere, chiede al progetto proprietario (o gerarchia) di salvare il documento. Ciò consente al progetto di salvare i dati dell'elemento di progetto in file locali, file remoti, un database, un repository o un altro supporto.

 L'ambiente globale mantiene il RDT. L'ambiente gestisce le voci per tutte le finestre aperte e documenti in RDT, che consente loro di ricevere notifiche speciali, ad esempio quando una soluzione viene chiusa. Inoltre, RDT consente all'ambiente di tenere traccia dei nodi corrispondenti in **Esplora soluzioni.** RDT gestisce un record per oggetto aperto e persistente, inclusi i file di progetto e i documenti degli elementi di progetto.

## <a name="see-also"></a>Vedere anche
- [Tabella documenti in esecuzione](../../extensibility/internals/running-document-table.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
