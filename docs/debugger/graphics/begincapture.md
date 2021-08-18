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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c9c461bdae97e1fd26491e72bad1791ce529e2ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052070"
---
# <a name="begincapture"></a>BeginCapture
Inizia un intervallo di acquisizione che terminerà con `EndCapture` .

## <a name="syntax"></a>Sintassi

```C++
void BeginCapture();
```

## <a name="remarks"></a>Osservazioni
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.

 Per acquisire un intervallo, è necessario preparare l'app per acquisire e registrare informazioni grafiche, ovvero è necessario aver chiamato [Init](init.md) tramite un'istanza della classe prima di `VsgDbg` chiamare o `BeginCapture` `EndCapture` .

## <a name="see-also"></a>Vedi anche
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)