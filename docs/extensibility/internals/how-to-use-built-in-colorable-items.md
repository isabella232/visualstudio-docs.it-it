---
title: 'Procedura: Usare Built-In colorabili | Microsoft Docs'
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
ms.openlocfilehash: 903a69eb19fb0d70558302aee4ae356ee65224ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063265"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: Usare elementi colorabili predefiniti
Prima di usare gli elementi colorabili predefiniti, è necessario segnalare all'ambiente di sviluppo integrato (IDE) di non fornire elementi colorabili personalizzati, che in questo caso sono oggetti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> . A tale scopo, impostare una voce del Registro di sistema per il servizio di linguaggio.

## <a name="to-use-built-in-colorable-items"></a>Per usare elementi colorabili predefiniti

1. In **HKEY_LOCAL_MACHINE\VisualStudio\\<X.Y>\Languages\Language Services \\<Language Name \>**, dove è una versione di e è il nome della lingua, creare un valore della voce del Registro di sistema DWORD denominato \<X.Y> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \<Language Name> **RequestStockColors**.

2. Impostare il valore della voce del Registro di sistema **RequestStockColors** su *1*.

    Dopo aver creato la voce del Registro di sistema, il metodo del colorista può usare i membri dell'enumerazione per compilare la matrice di attributi di colore per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> l'uso da parte dell'editor.

   > [!NOTE]
   > Non impostare questa voce del Registro di sistema se si specificano elementi colorabili personalizzati. Per altre informazioni, vedere [Elementi colorabili personalizzati.](../../extensibility/internals/custom-colorable-items.md)

## <a name="see-also"></a>Vedi anche
- [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)
- [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)
- [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)
- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)
