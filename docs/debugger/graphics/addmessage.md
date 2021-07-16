---
title: AddMessage | Microsoft Docs
description: Usare il metodo AddMessage della classe VsgDbg per aggiungere un messaggio personalizzato alla diagnostica grafica Head-Up display (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1046b7d8a71efb7d628302041a83fb9d20138a29
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232856"
---
# <a name="addmessage"></a>AddMessage
Aggiunge un messaggio personalizzato alla diagnostica grafica *HUD* (Head-Up Display).

## <a name="syntax"></a>Sintassi

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametri
 `szMessage` Messaggio da aggiungere a HUD.

## <a name="remarks"></a>Commenti
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Vengono visualizzate le informazioni di runtime sull'applicazione e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando questa funzione.

 Per aggiungere un messaggio a HUD, non è necessario acquisire attivamente informazioni grafiche, ovvero un messaggio può essere aggiunto tramite un'istanza della classe `VsgDbg`, ma la funzione membro [Init](init.md) non deve essere chiamata per prima. I messaggi vengono visualizzati solo in HUD, non vengono registrati nei file di log di grafica.