---
title: Supporto della procedura guidata per i progetti annidati | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703198"
---
# <a name="wizard-support-for-nested-projects"></a>Supporto di procedure guidate per i progetti annidati
L'IDE esegue due procedure guidate che il progetto padre per i progetti annidati può implementare: creazione guidata **nuovo progetto** e **Aggiunta guidata elemento** .

 Se un utente avvia la creazione guidata **nuovo progetto** selezionando **Aggiungi progetto** e scegliendo **nuovo progetto** dal menu file oppure selezionando **Aggiungi** e facendo clic con il pulsante destro del mouse su **nuovo progetto** in Esplora soluzioni, l'IDE esegue il comando **AddProject** e l'implementazione del progetto padre del comando **AddProject** restituisce un file di progetto di modello o un file con estensione vsz con un set di parametri di contesto.

 Analogamente, l'implementazione delle procedure guidate di un progetto padre restituisce un file con estensione vsz che **dispone di un** set diverso di parametri di contesto.

 Per ulteriori informazioni sulle procedure guidate, vedere [procedura guidata (. File VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md), [parametri di contesto](../../extensibility/internals/context-parameters.md) e [registrazione dei modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
