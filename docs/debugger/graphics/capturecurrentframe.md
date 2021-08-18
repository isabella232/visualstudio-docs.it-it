---
title: CaptureCurrentFrame | Microsoft Docs
description: Usare il metodo CaptureCurrentFrame della classe VsgDbg per acquisire il resto del frame corrente nel file di log grafico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0271ccd7b1a9a90ae683e86a141d41d269cac773
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154265"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Acquisisce il resto del frame corrente nel file di log di grafica.

## <a name="syntax"></a>Sintassi

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Osservazioni
 Se è attualmente in corso un'altra acquisizione, ad esempio un'acquisizione avviata dalla funzione `BeginCapture`, tale acquisizione viene completata e registrata nel log di grafica come frame distinto. Immediatamente dopo, la diagnostica della grafica inizia ad acquisire la parte restante del frame corrente, che viene a sua volta registrata come frame distinto. La fine del frame corrente viene contrassegnata da una chiamata da presentare.

 Per acquisire un frame, è necessario preparare l'app per acquisire e registrare informazioni grafiche, ovvero è necessario aver chiamato [Init tramite](init.md) un'istanza della classe prima di `VsgDbg` chiamare `CaptureCurrentFrame` .

## <a name="see-also"></a>Vedi anche
- [Init](init.md)
- [BeginCapture](begincapture.md)