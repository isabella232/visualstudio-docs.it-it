---
title: BeginCapture | Microsoft Docs
description: Usare il metodo BeginCapture della classe VsgDbg per iniziare un intervallo di acquisizione che terminerà con EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c9fc81bdd058d3a8c1dbe26bbe944bcb0e354ac7
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232738"
---
# <a name="begincapture"></a>BeginCapture
Inizia un intervallo di acquisizione che termina con `EndCapture` .

## <a name="syntax"></a>Sintassi

```C++
void BeginCapture();
```

## <a name="remarks"></a>Osservazioni
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.

 Per acquisire un intervallo, è necessario preparare l'app per acquisire e registrare informazioni grafiche, ovvero è necessario aver chiamato [Init tramite](init.md) un'istanza della classe prima di `VsgDbg` chiamare o `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Vedi anche
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)