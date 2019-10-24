---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736149"
---
# <a name="begincapture"></a>BeginCapture
Inizia un intervallo di acquisizione che terminerà con `EndCapture`.

## <a name="syntax"></a>Sintassi

```C++
void BeginCapture();
```

## <a name="remarks"></a>Note
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.

 Per acquisire un intervallo, è necessario preparare l'app per acquisire e registrare le informazioni grafiche, ovvero è necessario avere chiamato [init](init.md) tramite un'istanza della classe `VsgDbg` prima di chiamare `BeginCapture` o `EndCapture`.

## <a name="see-also"></a>Vedere anche
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)