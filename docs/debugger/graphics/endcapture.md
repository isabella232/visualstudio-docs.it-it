---
title: EndCapture | Microsoft Docs
description: Usare il metodo EndCapture della classe VsgDbg per terminare un intervallo di acquisizione avviato con BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8b0820950980860465e5129211c77e48ff641bdf
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232674"
---
# <a name="endcapture"></a>EndCapture
Termina un intervallo di acquisizione avviato con `BeginCapture`.

## <a name="syntax"></a>Sintassi

```C++
void EndCapture();
```

## <a name="remarks"></a>Osservazioni
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.

 Per acquisire un intervallo, è necessario preparare l'app per acquisire e registrare informazioni grafiche, ovvero è necessario aver chiamato [Init tramite](init.md) un'istanza della classe prima di `VsgDbg` chiamare o `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Vedi anche
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)