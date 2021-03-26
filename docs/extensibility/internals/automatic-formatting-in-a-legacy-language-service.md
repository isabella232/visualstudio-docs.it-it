---
title: Formattazione automatica in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulla formattazione automatica in un servizio di linguaggio legacy, che inserisce automaticamente un frammento di codice quando si inizia a digitare un costrutto di codice noto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a08a56a6820917b3a954c162b1875430875c7585
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086274"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione automatica in un servizio di linguaggio legacy
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noto.

## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica
 Se, ad esempio, si digita *se*, il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti o si preme il tasto invio, il servizio di linguaggio impone il punto di inserimento sulla nuova riga al livello di rientro appropriato, a seconda che la riga precedente apra un nuovo ambito.

 Il filtro dei comandi utilizzato per il resto del servizio di linguaggio può essere utilizzato anche per la formattazione automatica. È anche possibile evidenziare le parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Vedi anche
- [Sviluppare un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
