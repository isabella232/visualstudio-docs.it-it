---
title: 'Procedura: utilizzare elementi colorabili Built-In | Microsoft Docs'
description: Informazioni su come usare gli elementi colorabili incorporati in Visual Studio Integrated Development Environment (IDE) per il servizio di linguaggio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 926cb77fe9477b7dc78c35c2ab58f9b73530e4fa
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761010"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: utilizzare elementi colorabili incorporati
Prima di utilizzare gli elementi colorabili incorporati, è necessario innanzitutto segnalare all'Integrated Development Environment (IDE) che non si forniscono elementi colorabili personalizzati, che in questo caso sarebbero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> oggetti. A tale scopo, impostare una voce del registro di sistema per il servizio di linguaggio.

## <a name="to-use-built-in-colorable-items"></a>Per utilizzare elementi colorabili incorporati

1. In **HKEY_LOCAL_MACHINE\VisualStudio\\<X. Y> \languages\language Services \\<\> nome della lingua**, dove \<X.Y> è una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e \<Language Name> è il nome della lingua, creare un valore di voce del registro di sistema DWORD denominato **RequestStockColors**.

2. Impostare il valore della voce del registro di sistema **RequestStockColors** su *1*.

    Dopo aver creato la voce del registro di sistema, il metodo del coloratore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> può usare i membri dell' <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumerazione per compilare la matrice di attributi di colore per l'uso da parte dell'editor.

   > [!NOTE]
   > Non impostare questa voce del registro di sistema se si forniscono elementi colorabili personalizzati. Per altre informazioni, vedere [elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md).

## <a name="see-also"></a>Vedi anche
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)
