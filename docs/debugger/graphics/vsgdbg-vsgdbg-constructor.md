---
title: 'VsgDbg:: VsgDbg (costruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734753"
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
 `bDefaultInit` `true` per specificare che il componente di diagnostica della grafica integrato nell'applicazione deve essere preparato per acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che in questo momento l'applicazione non deve essere preparata per acquisire e registrare attivamente le informazioni grafiche.

## <a name="remarks"></a>Note
 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `true`, il nome file del file di log di grafica è determinato dalla modalità di definizione dei simboli del preprocessore `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` prima che `vsgcapture.h` sia incluso nell'app.

 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `false`, il componente di diagnostica della grafica integrato nell'applicazione può essere preparato per acquisire e registrare attivamente le informazioni grafiche in un secondo momento chiamando la funzione `Init`.

## <a name="see-also"></a>Vedere anche
- [VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)