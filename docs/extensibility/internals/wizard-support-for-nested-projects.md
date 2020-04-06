---
title: Supporto della procedura guidata per i progetti nidificati . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703198"
---
# <a name="wizard-support-for-nested-projects"></a>Supporto di procedure guidate per i progetti annidati
L'IDE esegue due procedure guidate che il progetto padre per i progetti annidati può implementare: la creazione guidata **nuovo progetto** e la procedura guidata **Aggiungi elemento.**

 Se un utente avvia la procedura guidata **Nuovo progetto** selezionando **Aggiungi progetto** e scegliendo Nuovo **progetto** dal menu File o scegliendo **Aggiungi** e facendo clic con il pulsante destro del mouse su **Nuovo progetto** in Esplora soluzioni, l'IDE esegue il comando **AggiungiProgetto** e l'implementazione del progetto padre del comando **AggiungiProgetto** restituisce un file di progetto modello o un file di procedura guidata (vsz) con un set di parametri di contesto.

 Analogamente, l'implementazione di un progetto padre delle procedure guidate **AddItem** restituisce un file vsz con un set diverso di parametri di contesto.

 Per altre informazioni sulle procedure guidate, vedere [Wizard (. Vsz) File](../../extensibility/internals/wizard-dot-vsz-file.md), [Parametri di contesto](../../extensibility/internals/context-parameters.md) e [Registrazione dei modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
