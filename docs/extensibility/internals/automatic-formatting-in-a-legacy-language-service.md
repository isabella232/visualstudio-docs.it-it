---
title: La formattazione automatica in un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56910a984fabb3ac4825fd438be17745126692a6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500670"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione automatica in un servizio di linguaggio legacy
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noto.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica  
 Ad esempio, quando si digita *se*, il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti o se si preme il tasto INVIO, il servizio di linguaggio forza il punto di inserimento nella nuova riga per il livello di rientro appropriato, a seconda indica se la riga precedente viene aperto un nuovo ambito.  
  
 Il filtro di comando utilizzato per il resto del servizio di linguaggio è anche utilizzabile per la formattazione automatica. È anche possibile evidenziare le parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppare un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)