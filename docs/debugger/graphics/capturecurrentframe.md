---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736127"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Acquisisce il resto del frame corrente nel file di log di grafica.

## <a name="syntax"></a>Sintassi

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Note
 Se è attualmente in corso un'altra acquisizione, ad esempio un'acquisizione avviata dalla funzione `BeginCapture`, tale acquisizione viene completata e registrata nel log di grafica come frame distinto. Immediatamente dopo, la diagnostica della grafica inizia ad acquisire la parte restante del frame corrente, che viene a sua volta registrata come frame distinto. La fine del frame corrente viene contrassegnata da una chiamata da presentare.

 Per acquisire un frame, è necessario preparare l'app per acquisire e registrare le informazioni grafiche, ovvero è necessario avere chiamato [init](init.md) tramite un'istanza della classe `VsgDbg` prima di chiamare `CaptureCurrentFrame`.

## <a name="see-also"></a>Vedere anche
- [Init](init.md)
- [BeginCapture](begincapture.md)