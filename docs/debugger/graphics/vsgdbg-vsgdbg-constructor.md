---
description: Costruisce un'istanza della classe VsgDbg con o senza preparare il componente in-app di diagnostica grafica per acquisire e registrare attivamente le informazioni grafiche per impostazione predefinita, in base al parametro booleano specificato.
title: VsgDbg::VsgDbg (costruttore) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: bd927b7f271549622e77c39ed83cdb1ebe14cd57
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161342"
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
 `bDefaultInit``true`per specificare che il componente in-app della diagnostica grafica deve essere preparato per acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che l'app non deve essere preparata per acquisire e registrare attivamente le informazioni grafiche in questo momento.

## <a name="remarks"></a>Commenti
 Quando il costruttore viene chiamato con impostato su , il nome file del file di log grafico è determinato dal modo in cui i simboli del preprocessore e vengono definiti prima di essere `bDefaultInit` `true` inclusi `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` `vsgcapture.h` nell'app.

 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `false`, il componente di diagnostica della grafica integrato nell'applicazione può essere preparato per acquisire e registrare attivamente le informazioni grafiche in un secondo momento chiamando la funzione `Init`.

## <a name="see-also"></a>Vedi anche
- [VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
