---
title: 'Vsgdbg:: Vsgdbg (costruttore) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4c4c987bd0f44f6b8a4bad945d249aaf832fc57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035276"
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
 `bDefaultInit`  
 `true` per specificare che il componente di diagnostica della grafica integrato nell'applicazione deve essere preparato per acquisire e registrare attivamente le informazioni grafiche; `false` per specificare che in questo momento l'applicazione non deve essere preparata per acquisire e registrare attivamente le informazioni grafiche.  
  
## <a name="remarks"></a>Note  
 Quando il costruttore viene chiamato con `bDefaultInit` impostata su `true`, il nome file del file di log di grafica viene determinato dal modo in cui `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` vengono definiti i simboli del preprocessore prima `vsgcapture.h` è incluso nell'app.  
  
 Quando il costruttore viene chiamato con `bDefaultInit` impostato su `false`, il componente di diagnostica della grafica integrato nell'applicazione può essere preparato per acquisire e registrare attivamente le informazioni grafiche in un secondo momento chiamando la funzione `Init`.  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)