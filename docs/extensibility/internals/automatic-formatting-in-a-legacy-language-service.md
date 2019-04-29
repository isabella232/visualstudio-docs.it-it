---
title: La formattazione automatica in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64fbf5b64b57425b1bdee3ae3475c234384db062
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910605"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione automatica in un servizio di linguaggio legacy
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noto.

## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica
 Ad esempio, quando si digita *se*, il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti o se si preme il tasto INVIO, il servizio di linguaggio forza il punto di inserimento nella nuova riga per il livello di rientro appropriato, a seconda indica se la riga precedente viene aperto un nuovo ambito.

 Il filtro di comando utilizzato per il resto del servizio di linguaggio è anche utilizzabile per la formattazione automatica. È anche possibile evidenziare le parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.

## <a name="see-also"></a>Vedere anche
- [Sviluppare un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)