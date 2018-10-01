---
title: Classe VsgDbg | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 927990cb8fb21dfeaf25a681cfb0a222ecc3c8ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517176"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [classe VsgDbg](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-class).  
  
Rappresenta un'interfaccia per il controllo a livello di codice del componente in-app di diagnostica della grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Membri  
 Il `VsgDbg` classe supporta i seguenti membri.  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (Costruttore)](../debugger/vsgdbg-vsgdbg-constructor.md)|Costruisce un'istanza di `VsgDbg` classe e, facoltativamente, Prepara il componente in-app di diagnostica della grafica per acquisire e registrare le informazioni grafiche attivamente.|  
|[VsgDbg::~VsgDbg (distruttore)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Elimina un'istanza di `VsgDbg` classe.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Aggiunge un messaggio personalizzato alla diagnostica della grafica HUD (Head-Up Display).|  
|[BeginCapture](../debugger/begincapture.md)|Inizia un intervallo di acquisizione che termina con `EndCapture`.|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Acquisisce il resto del frame corrente nel file di log di grafica.|  
|[Copia (acquisizione a livello di codice)](../debugger/copy-programmatic-capture.md)|Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.|  
|[EndCapture](../debugger/endcapture.md)|Termina un intervallo di acquisizione avviato con `BeginCapture`.|  
|[Init](../debugger/init.md)|Prepara il componente in-app di diagnostica della grafica per acquisire e registrare le informazioni grafiche attivamente.|  
|[ToggleHUD](../debugger/togglehud.md)|Attiva o disattiva la sovrimpressione HUD di diagnostica della grafica o disattivare.|  
|[UnInit](../debugger/uninit.md)|Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.|  
  
## <a name="remarks"></a>Note  
 Il `VsgDbg` classe rappresenta un'interfaccia che è possibile usare per controllare le funzionalità di diagnostica della grafica a livello di codice. È possibile usare alcune funzionalità anche quando si sta attivamente acquisire e registrare le informazioni grafiche; Ciò include la `AddMessage` funzione membro e `ToggleHUD` funzione membro. Le altre funzioni membro preparare il componente in-app di diagnostica della grafica per avviare o arrestare l'acquisizione di informazioni grafiche attivo oppure devono essere chiamate mentre l'app è attivamente acquisire e registrare le informazioni grafiche in un file di log di grafica.



