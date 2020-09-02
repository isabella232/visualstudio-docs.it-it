---
title: Classe VsgDbg | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 053647d48324f056148375bae9268b997ba8721f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145700"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rappresenta un'interfaccia per il controllo a livello di codice del componente in-app della diagnostica grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
class VsgDbg;  
```  
  
## <a name="members"></a>Membri  
 La `VsgDbg` classe supporta i membri seguenti.  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[VsgDbg::VsgDbg (costruttore)](../debugger/vsgdbg-vsgdbg-constructor.md)|Costruisce un'istanza della `VsgDbg` classe e, facoltativamente, prepara il componente in-app della diagnostica della grafica per acquisire e registrare attivamente le informazioni grafiche.|  
|[VsgDbg::~VsgDbg (distruttore)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|Elimina un'istanza della `VsgDbg` classe.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[AddMessage](../debugger/addmessage.md)|Aggiunge un messaggio personalizzato alla diagnostica della grafica HUD (Head-Up Display).|  
|[BeginCapture](../debugger/begincapture.md)|Inizia un intervallo di acquisizione che termina con `EndCapture` .|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|Acquisisce il resto del frame corrente nel file di log di grafica.|  
|[Copia (acquisizione a livello di codice)](../debugger/copy-programmatic-capture.md)|Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.|  
|[EndCapture](../debugger/endcapture.md)|Termina un intervallo di acquisizione avviato con `BeginCapture`.|  
|[Init](../debugger/init.md)|Prepara il componente in-app della diagnostica della grafica per acquisire e registrare attivamente le informazioni grafiche.|  
|[ToggleHUD](../debugger/togglehud.md)|Attiva o disattiva la sovrimpressione HUD di diagnostica della grafica.|  
|[UnInit](../debugger/uninit.md)|Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.|  
  
## <a name="remarks"></a>Osservazioni  
 La `VsgDbg` classe rappresenta un'interfaccia che è possibile usare per controllare le funzionalità di diagnostica della grafica a livello di codice. È possibile usare alcune funzionalità anche quando non si acquisisce e si registrano attivamente le informazioni grafiche; sono incluse la `AddMessage` funzione membro e la `ToggleHUD` funzione membro. Le altre funzioni membro preparano il componente in-app della diagnostica della grafica per avviare o arrestare l'acquisizione attiva delle informazioni grafiche oppure deve essere chiamato mentre l'app acquisisce e registra attivamente le informazioni grafiche in un file di log di grafica.
