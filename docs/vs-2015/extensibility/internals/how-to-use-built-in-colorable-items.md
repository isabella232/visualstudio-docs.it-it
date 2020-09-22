---
title: 'Procedura: utilizzare elementi colorabili predefiniti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a86361f28eb4c73a65093fc5c80ef15ddf791a77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839407"
---
# <a name="how-to-use-built-in-colorable-items"></a>Procedura: Usare gli elementi colorabili incorporati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prima di utilizzare gli elementi colorabili incorporati, è necessario innanzitutto segnalare all'Integrated Development Environment (IDE) che non si forniscono elementi colorabili personalizzati, che in questo caso sarebbero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> oggetti. A tale scopo, impostare una voce del registro di sistema per il servizio di linguaggio.  
  
### <a name="to-use-built-in-colorable-items"></a>Per utilizzare elementi colorabili incorporati  
  
1. In HKEY_LOCAL_MACHINE \VisualStudio \\ *X. y*\Languages\Language Services \\ *Language Name*, dove *X. y* è una versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e *nome lingua* è il nome della lingua, creare un valore di voce del registro di sistema DWORD denominato `RequestStockColors` .  
  
2. Impostare il `RequestStockColors` valore della voce del registro di sistema su 1.  
  
     Dopo aver creato la voce del registro di sistema, il metodo del coloratore <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> può usare i membri dell' <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> enumerazione per compilare la matrice di attributi di colore per l'uso da parte dell'editor.  
  
    > [!NOTE]
    > Non impostare questa voce del registro di sistema se si forniscono elementi colorabili personalizzati. Per altre informazioni, vedere [elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Colorazione della sintassi negli editor personalizzati](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [Colorazione della sintassi in un servizio di linguaggio legacy](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione della colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Elementi colorabili personalizzati](../../extensibility/internals/custom-colorable-items.md)   
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service2.md)
