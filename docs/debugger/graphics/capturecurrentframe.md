---
title: CaptureCurrentFrame | Microsoft Docs
description: Usare il metodo CaptureCurrentFrame della classe VsgDbg per acquisire il resto del frame corrente nel file di log di grafica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c55a34ee71f8002d31613d64ff978f0a546b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874548"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Acquisisce il resto del frame corrente nel file di log di grafica.

## <a name="syntax"></a>Sintassi

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Osservazioni
 Se è attualmente in corso un'altra acquisizione, ad esempio un'acquisizione avviata dalla funzione `BeginCapture`, tale acquisizione viene completata e registrata nel log di grafica come frame distinto. Immediatamente dopo, la diagnostica della grafica inizia ad acquisire la parte restante del frame corrente, che viene a sua volta registrata come frame distinto. La fine del frame corrente viene contrassegnata da una chiamata da presentare.

 Per acquisire un frame, è necessario preparare l'app per acquisire e registrare le informazioni grafiche, ovvero è necessario avere chiamato [init](init.md) tramite un'istanza della `VsgDbg` classe prima di chiamare `CaptureCurrentFrame` .

## <a name="see-also"></a>Vedi anche
- [Init](init.md)
- [BeginCapture](begincapture.md)