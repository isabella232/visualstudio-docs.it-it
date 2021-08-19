---
title: AddMessage | Microsoft Docs
description: Usare il metodo AddMessage della classe VsgDbg per aggiungere un messaggio personalizzato alla diagnostica grafica Head-Up Display (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 98b37dd5df91bd4907869c36e40938a075d67396
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138978"
---
# <a name="addmessage"></a>AddMessage
Aggiunge un messaggio personalizzato *all'HUD* di diagnostica grafica (Visualizzazione head-up).

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