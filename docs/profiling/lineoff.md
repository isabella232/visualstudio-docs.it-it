---
title: LineOff | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4de8aa278adab0127f3a39d9adcf105f906e152
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625244"
---
# <a name="lineoff"></a>LineOff
Per impostazione predefinita, il profiler raccoglie i dati dei numeri di riga del codice sorgente e i dati di offset dei numeri di riga quando si usa il metodo di campionamento per la profilatura. L'opzione **LineOff** di VSPerfCmd disabilita la raccolta dei dati dei numeri di riga quando VSPerfCmd viene usato per avviare l'applicazione. I dati di profilatura vengono raccolti a livello di funzione quando si specifica l'opzione **LineOff**.

 È possibile usare **LineOff** solo con l'opzione **Launch** e solo quando il profiler è stato inizializzato per eseguire il campionamento tramite l'opzione **Start**:**Sample**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **LineOff** può essere usata solo su una riga di comando che contiene l'opzione **Launch**.

 **Launch:** `AppName` Avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

## <a name="example"></a>Esempio
 Questo esempio illustra come avviare l'applicazione e il profiler e quindi disabilitare il campionamento a livello di riga.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)