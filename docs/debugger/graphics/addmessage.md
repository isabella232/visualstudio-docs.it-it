---
title: AddMessage | Microsoft Docs
description: Usare il Metodo AddMessage della classe VsgDbg per aggiungere un messaggio personalizzato alla diagnostica della grafica Head-Up display (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efd4b29e6a4875611603087a1a2c0942c3e571b3
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727991"
---
# <a name="addmessage"></a>AddMessage
Aggiunge un messaggio personalizzato alla diagnostica della grafica *HUD* (Head-up display).

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