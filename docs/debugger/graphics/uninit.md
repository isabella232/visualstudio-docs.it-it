---
title: UnInit | Microsoft Docs
description: Usare il Metodo Uninit () di VsgDbg per finalizzare e chiudere il file di log di grafica e liberare le risorse di registrazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f79b39ced4f3285815412b9b231692868e5e00f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996058"
---
# <a name="uninit"></a>UnInit
Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.

## <a name="syntax"></a>Sintassi

```C++
void UnInit();
```

## <a name="remarks"></a>Osservazioni
 `UnInit` viene automaticamente chiamata quando viene eliminata definitivamente un'istanza della classe `VsgDbg`. Se l'istanza `VsgDbg` non stava registrando attivamente le informazioni grafiche, questa operazione non ha effetto.

 Una volta chiamata `UnInit` su un'istanza della classe `VsgDbg`, è possibile creare e un nuovo file di log di grafica chiamando `Init` e finalizzarlo chiamando `UnInit`. È possibile ripetere questa procedura tutte le volte che si desidera utilizzare la stessa istanza `VsgDbg` per creare diversi file di log di grafica indipendenti.

## <a name="see-also"></a>Vedere anche
- [Init](init.md)