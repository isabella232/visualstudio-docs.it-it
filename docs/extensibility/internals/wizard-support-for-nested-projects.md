---
title: Supporto della procedura guidata per i progetti annidati | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721428"
---
# <a name="wizard-support-for-nested-projects"></a>Supporto di procedure guidate per i progetti annidati
L'IDE esegue due procedure guidate che il progetto padre per i progetti annidati può implementare: creazione guidata **nuovo progetto** e **Aggiunta guidata elemento** .

 Se un utente avvia la creazione guidata **nuovo progetto** selezionando **Aggiungi progetto** e scegliendo **nuovo progetto** dal menu file oppure selezionando **Aggiungi** e facendo clic con il pulsante destro del mouse su **nuovo progetto** in Esplora soluzioni, l'IDE esegue il **AddProject** il comando e l'implementazione del progetto padre del comando **AddProject** restituiscono un file di progetto di modello o un file di procedura guidata (VSZ) con un set di parametri di contesto.

 Analogamente, l'implementazione delle procedure guidate di un progetto padre restituisce un file con estensione vsz che **dispone di un** set diverso di parametri di contesto.

 Per ulteriori informazioni sulle procedure guidate, vedere [procedura guidata (. File VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md), [parametri di contesto](../../extensibility/internals/context-parameters.md) e [registrazione dei modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)