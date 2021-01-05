---
title: BeginCapture | Microsoft Docs
description: Usare il metodo BeginCapture della classe VsgDbg per iniziare un intervallo di acquisizione che termina con EndCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 931e7ab05442a429c0b9e6468d42aadca942c1ee
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727965"
---
# <a name="begincapture"></a>BeginCapture
Inizia un intervallo di acquisizione che termina con `EndCapture` .

## <a name="syntax"></a>Sintassi

```C++
void BeginCapture();
```

## <a name="remarks"></a>Osservazioni
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.

 Per acquisire un intervallo, è necessario preparare l'app per acquisire e registrare le informazioni grafiche, ovvero è necessario avere chiamato [init](init.md) tramite un'istanza della `VsgDbg` classe prima di chiamare `BeginCapture` o `EndCapture` .

## <a name="see-also"></a>Vedi anche
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)