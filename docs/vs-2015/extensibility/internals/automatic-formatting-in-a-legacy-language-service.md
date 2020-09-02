---
title: Formattazione automatica in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157266"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione automatica in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noto.  
  
## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica  
 Quando si digita, ad esempio `if` , il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti o si preme il tasto invio, il servizio di linguaggio impone il punto di inserimento sulla nuova riga al livello di rientro appropriato, a seconda che la riga precedente apra un nuovo ambito.  
  
 Il filtro dei comandi utilizzato per il resto del servizio di linguaggio può essere utilizzato anche per la formattazione automatica. È anche possibile evidenziare le parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
