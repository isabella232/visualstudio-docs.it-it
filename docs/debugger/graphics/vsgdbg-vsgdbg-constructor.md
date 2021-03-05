---
description: Costruisce un'istanza della classe VsgDbg con o senza preparare il componente in-app della diagnostica grafica per acquisire e registrare attivamente le informazioni grafiche per impostazione predefinita, in base al parametro booleano specificato.
title: 'VsgDbg:: VsgDbg (costruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae4259b1af1bcb51b05431131db596d2a26da895
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160446"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (costruttore)
Costruisce un'istanza della classe `VsgDbg` con o senza la preparazione del componente della diagnostica della grafica integrato nell'applicazione per acquisire e registrare attivamente le informazioni grafiche per impostazione predefinita, in base al parametro booleano specificato.

## <a name="syntax"></a>Sintassi

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parametri
 `bDefaultInit``true`per specificare che il componente in-app della diagnostica della grafica deve essere preparato per acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che l'app non deve essere preparata per acquisire e registrare attivamente le informazioni grafiche in questo momento.

## <a name="remarks"></a>Commenti
 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `true` , il nome file del file di log di grafica è determinato dalla modalità `DONT_SAVE_VSGLOG_TO_TEMP` di `VSG_DEFAULT_RUN_FILENAME` definizione dei simboli del preprocessore e prima che `vsgcapture.h` sia incluso nell'app.

 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `false`, il componente di diagnostica della grafica integrato nell'applicazione può essere preparato per acquisire e registrare attivamente le informazioni grafiche in un secondo momento chiamando la funzione `Init`.

## <a name="see-also"></a>Vedi anche
- [VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
