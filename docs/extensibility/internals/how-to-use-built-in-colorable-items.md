---
title: 'Procedura: utilizzare elementi colorabili predefiniti | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 762d1e53f7aafa11ed345859e68fc98766eec77d
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905214"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: utilizzare elementi colorabili incorporati
Prima di utilizzare gli elementi colorabili incorporati, è necessario innanzitutto segnalare all'Integrated Development Environment (IDE) che non si forniscono elementi colorabili personalizzati, che in questo caso sarebbero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> oggetti. A tale scopo, impostare una voce del registro di sistema per il servizio di linguaggio.

## <a name="to-use-built-in-colorable-items"></a>Per utilizzare elementi colorabili incorporati

1. In **HKEY_LOCAL_MACHINE \visualstudio \\<X. Y> \languages\language Services \\<nome \> della lingua**, dove \<X.Y> è una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e \<Language Name> è il nome della lingua in uso, creare un valore di voce del registro di sistema DWORD denominato **RequestStockColors**.

2. Impostare il valore della voce del registro di sistema **RequestStockColors** su *1*.

    Dopo aver creato la voce del registro di sistema, il metodo del coloratore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> può usare i membri dell' <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumerazione per compilare la matrice di attributi di colore per l'uso da parte dell'editor.

   > [!NOTE]
   > Non impostare questa voce del registro di sistema se si forniscono elementi colorabili personalizzati. Per altre informazioni, vedere [elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Vedere anche
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)
