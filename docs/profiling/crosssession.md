---
title: CrossSession | Microsoft Docs
description: Informazioni su come usare l'VSPerfCmd.exe CrossSession per consentire al profiler di raccogliere dati da qualsiasi sessione della console. È necessario specificare anche l'opzione Start.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4dffc4946f0476bb9b93f39392d310ced5c8e824
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637220"
---
# <a name="crosssession"></a>CrossSession
 **LVSPerfCmd.exe'opzione CrossSession** consente al profiler di raccogliere dati da qualsiasi sessione della console. L'opzione **CrossSession** deve essere usata con l'opzione **Start**.

 È possibile usare l'abbreviazione **CS** al posto di **CrossSession**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="valid-options"></a>Opzioni valide
 Per abilitare la profilatura in un'altra sessione, l'opzione **CrossSession** deve essere specificata con l'opzione **Start**. **CrossSession** deve essere specificata anche in tutti i comandi **Attach e Detach** di **VSPerfCmd**.

 **Avvio:** `Method` **L'opzione Start** inizializza il profiler sul metodo di profilatura specificato.

 **Attach:** _PID_[**,**_PID_] Avvia la profilatura dei processi specificati.

 **Detach**[**:**_PID_[,_PID_]] Arresta la profilatura dei processi specificati.

## <a name="example"></a>Esempio
 In questo esempio l'opzione **CrossSession** viene usata per connettersi a un'applicazione che è stata avviata in un'altra sessione di console.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
