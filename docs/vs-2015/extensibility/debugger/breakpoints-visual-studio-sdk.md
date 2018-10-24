---
title: I punti di interruzione (Visual Studio SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 783e996ce0a2b1d1761bc765f7748794487364c6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827611"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punti di interruzione (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esistono tre tipi di punti di interruzione: in sospeso, associazione e di errore.  
  
 **Oggetto in sospeso punto di interruzione:**  
  
- È un'astrazione che contiene tutte le informazioni necessarie per associare un punto di interruzione a uno o più contesti di codice in uno o più programmi. Ogni volta che un programma in fase di debug causa codice per caricare, il motore di debug controlla tutti i punti di interruzione in sospeso per vedere se può essere associati.  
  
   Un punto di interruzione in sospeso stesso mai associa al codice, ma piuttosto raccoglie e si dice che contiene tutti i punti di interruzione associati che genera.  
  
- È rappresentato da un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia.  
  
  **Un punto di interruzione associato:**  
  
- È un'astrazione per un punto di interruzione associata o associata a un contesto di codice singolo. Ogni punto di interruzione associato viene generato in risposta a un punto di interruzione in sospeso. Un punto di interruzione in sospeso può, tuttavia, generare più di un punto di interruzione associato.  
  
   Quando il codice scaricato, un punto di interruzione associato può annullare l'associazione e rimossi.  
  
- È rappresentato da un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaccia.  
  
  **Un punto di interruzione di errore:**  
  
- È un'astrazione per la descrizione di un errore nel tentativo di associare un punto di interruzione in sospeso a un contesto del codice. Un punto di interruzione di errore descrive un errore nel percorso o nell'espressione di punto di interruzione se stesso. Per altre informazioni, vedere [associazione di punti di interruzione](../../extensibility/debugger/binding-breakpoints.md).  
  
   L'errore punto di interruzione può essere un errore o un avviso.  
  
- È rappresentato da un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

