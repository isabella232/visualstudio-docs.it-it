---
title: 'Procedura: Usare elementi Built-In colorabili | Microsoft Docs'
description: Informazioni su come usare gli elementi colorabili predefiniti nel Visual Studio di sviluppo integrato (IDE) per il servizio di linguaggio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ea6982d854380b8722e395db11f2ac5099a9bc26dd972ea0730cfbfeef586303
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388669"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: Usare elementi colorabili predefiniti
Prima di usare gli elementi colorabili predefiniti, è necessario segnalare all'ambiente di sviluppo integrato (IDE) di non fornire elementi colorabili personalizzati, che in questo caso sarebbero oggetti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> . A tale scopo, impostare una voce del Registro di sistema per il servizio di linguaggio.

## <a name="to-use-built-in-colorable-items"></a>Per usare elementi colorabili predefiniti

1. In **HKEY_LOCAL_MACHINE\VisualStudio\\<X.Y>\Languages\Language Services \\<Language Name \>**, dove è una versione di e è il nome della lingua, creare un valore di voce del Registro di sistema \<X.Y> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<Language Name> DWORD denominato **RequestStockColors**.

2. Impostare il valore della voce del Registro di sistema **RequestStockColors** su *1.*

    Dopo aver creato la voce del Registro di sistema, il metodo del colorizer può usare i membri dell'enumerazione per compilare la matrice di attributi di colore da usare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> dall'editor.

   > [!NOTE]
   > Non impostare questa voce del Registro di sistema se si forniscono elementi colorabili personalizzati. Per altre informazioni, vedere [Elementi colorabili personalizzati.](../../extensibility/internals/custom-colorable-items.md)

## <a name="see-also"></a>Vedi anche
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)
