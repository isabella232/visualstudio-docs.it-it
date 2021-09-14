---
title: Supporto della procedura guidata per progetti annidati | Microsoft Docs
description: Informazioni sulle due procedure guidate che un progetto padre può implementare per i progetti annidati nel pacchetto VSPackage in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c0fdc97b8ef15b4fdfd8fee13affb52b1935b80f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711726"
---
# <a name="wizard-support-for-nested-projects"></a>Supporto di procedure guidate per i progetti annidati
L'IDE esegue due procedure guidate che il progetto padre per i **progetti annidati** può implementare: la procedura guidata Project e la **procedura guidata Aggiungi** elemento.

 Se un utente avvia la procedura guidata Nuovo **Project** selezionando Aggiungi **Project** e scegliendo Nuovo **Project** dal menu File o scegliendo Aggiungi e facendo clic con il pulsante destro del mouse su Nuovo **Project** in Esplora soluzioni, l'IDE esegue il comando **AggiungiProgetto** e l'implementazione del progetto padre del comando **AggiungiProgetto** restituisce un file di progetto modello o un file della procedura guidata (vsz) con un set di parametri di contesto. 

 Analogamente, l'implementazione delle procedure guidate **AddItem** di un progetto padre restituisce un file con estensione vsz con un set diverso di parametri di contesto.

 Per altre informazioni sulle procedure guidate, vedere [Procedura guidata (. Vsz) File](../../extensibility/internals/wizard-dot-vsz-file.md), [parametri di contesto](../../extensibility/internals/context-parameters.md) e registrazione Project modelli di [elemento](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [Annidamento dei progetti](../../extensibility/internals/nesting-projects.md)
