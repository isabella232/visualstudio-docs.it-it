---
description: Rappresenta un'interfaccia per il controllo a livello di codice del componente in-app della diagnostica grafica.
title: Classe VsgDbg | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ff1383b8ff7fdf1557415cda2616ecbfd7d2585a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080858"
---
# <a name="vsgdbg-class"></a>Classe VsgDbg
Rappresenta un'interfaccia per il controllo a livello di codice del componente in-app della diagnostica grafica.

## <a name="syntax"></a>Sintassi

```C++
class VsgDbg;
```

## <a name="members"></a>Members
 La `VsgDbg` classe supporta i membri seguenti.

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[VsgDbg::VsgDbg (costruttore)](vsgdbg-vsgdbg-constructor.md)|Costruisce un'istanza della classe e, facoltativamente, prepara il componente in-app della diagnostica grafica per acquisire e registrare attivamente le `VsgDbg` informazioni grafiche.|
|[VsgDbg::~VsgDbg (distruttore)](vsgdbg-tilde-vsgdbg-destructor.md)|Elimina un'istanza della `VsgDbg` classe .|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[AddMessage](addmessage.md)|Aggiunge un messaggio personalizzato alla diagnostica della grafica HUD (Head-Up Display).|
|[BeginCapture](begincapture.md)|Inizia un intervallo di acquisizione che termina con `EndCapture` .|
|[CaptureCurrentFrame](capturecurrentframe.md)|Acquisisce il resto del frame corrente nel file di log di grafica.|
|[Copia (acquisizione a livello di codice)](copy-programmatic-capture.md)|Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.|
|[EndCapture](endcapture.md)|Termina un intervallo di acquisizione avviato con `BeginCapture`.|
|[Init](init.md)|Prepara il componente in-app della diagnostica grafica per acquisire e registrare attivamente le informazioni grafiche.|
|[ToggleHUD](togglehud.md)|Attiva o disattiva la sovrapposizione HUD diagnostica grafica.|
|[UnInit](uninit.md)|Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.|

## <a name="remarks"></a>Commenti
 La `VsgDbg` classe rappresenta un'interfaccia che è possibile usare per controllare le funzionalità di diagnostica della grafica a livello di codice. È possibile usare alcune funzionalità anche quando non si acquisisce e si registrano attivamente informazioni grafiche. include la funzione `AddMessage` membro e la funzione `ToggleHUD` membro. Le altre funzioni membro preparano il componente in-app della diagnostica grafica per avviare o arrestare l'acquisizione attiva delle informazioni grafiche oppure devono essere chiamate mentre l'app acquisisce e registra attivamente le informazioni grafiche in un file di log grafico.
