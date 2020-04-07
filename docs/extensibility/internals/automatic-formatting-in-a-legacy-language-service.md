---
title: Formattazione automatica in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709985"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formattazione automatica in un servizio di linguaggio legacy
Con la formattazione automatica, un servizio di linguaggio inserisce automaticamente un frammento di codice quando un utente inizia a digitare un costrutto di codice noto.

## <a name="automatic-formatting-behavior"></a>Comportamento di formattazione automatica
 Ad esempio, quando si digita *if ,* il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti o se si preme il tasto INVIO, il servizio di linguaggio forza il punto di inserimento nella nuova riga al livello di rientro appropriato, a seconda che la riga precedente apra o meno un nuovo ambito.

 Il filtro di comando utilizzato per il resto del servizio di linguaggio può essere utilizzato anche per la formattazione automatica. È inoltre possibile evidenziare le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>parentesi graffe corrispondenti chiamando .

## <a name="see-also"></a>Vedere anche
- [Sviluppare un servizio di linguaggio legacyDevelop a legacy language service](../../extensibility/internals/developing-a-legacy-language-service.md)
