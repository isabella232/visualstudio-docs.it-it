---
title: Classe VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4051a02de6a046621e62c21b4d2399b5a2703cb8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714803"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
Rappresenta un'interfaccia per il controllo a livello di codice del componente in-app di diagnostica della grafica.

## <a name="syntax"></a>Sintassi

```C++
class VsgDbg;
```

## <a name="members"></a>Membri
 Il `VsgDbg` classe supporta i seguenti membri.

### <a name="public-constructors"></a>Costruttori pubblici

|nome|Description|
|----------|-----------------|
|[VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)|Costruisce un'istanza di `VsgDbg` classe e, facoltativamente, Prepara il componente in-app di diagnostica della grafica per acquisire e registrare le informazioni grafiche attivamente.|
|[VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)|Elimina un'istanza di `VsgDbg` classe.|

### <a name="public-methods"></a>Metodi pubblici

|nome|Description|
|----------|-----------------|
|[AddMessage](addmessage.md)|Aggiunge un messaggio personalizzato alla diagnostica della grafica HUD (Head-Up Display).|
|[BeginCapture](begincapture.md)|Inizia un intervallo di acquisizione che termina con `EndCapture`.|
|[CaptureCurrentFrame](capturecurrentframe.md)|Acquisisce il resto del frame corrente nel file di log di grafica.|
|[Copia (acquisizione a livello di codice)](copy-programmatic-capture.md)|Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.|
|[EndCapture](endcapture.md)|Termina un intervallo di acquisizione avviato con `BeginCapture`.|
|[Init](init.md)|Prepara il componente in-app di diagnostica della grafica per acquisire e registrare le informazioni grafiche attivamente.|
|[ToggleHUD](togglehud.md)|Attiva o disattiva la sovrimpressione HUD di diagnostica della grafica o disattivare.|
|[UnInit](uninit.md)|Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.|

## <a name="remarks"></a>Osservazioni
 Il `VsgDbg` classe rappresenta un'interfaccia che è possibile usare per controllare le funzionalità di diagnostica della grafica a livello di codice. È possibile usare alcune funzionalità anche quando si sta attivamente acquisire e registrare le informazioni grafiche; Ciò include la `AddMessage` funzione membro e `ToggleHUD` funzione membro. Le altre funzioni membro preparare il componente in-app di diagnostica della grafica per avviare o arrestare l'acquisizione di informazioni grafiche attivo oppure devono essere chiamate mentre l'app è attivamente acquisire e registrare le informazioni grafiche in un file di log di grafica.