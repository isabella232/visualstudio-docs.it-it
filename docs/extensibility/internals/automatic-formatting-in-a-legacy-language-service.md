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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1d5e824c96860030f0299fe6e1178515b7d1693d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124802"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione automatica in un servizio di linguaggio legacy
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noto.

## <a name="automatic-formatting-behavior"></a>Comportamento della formattazione automatica
 Ad esempio, quando si digita se *,* il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti o se si preme INVIO, il servizio di linguaggio forza il punto di inserimento nella nuova riga al livello di rientro appropriato, a seconda che la riga precedente apra un nuovo ambito.

 Il filtro comandi usato per il resto del servizio di linguaggio può essere usato anche per la formattazione automatica. È anche possibile evidenziare le parentesi graffe corrispondenti chiamando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Vedi anche
- [Sviluppare un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
