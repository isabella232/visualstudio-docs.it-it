---
title: Start | Microsoft Docs
description: Informazioni su come l'opzione Start VSPerfCmd.exe'opzione che inizializza il profiler sul metodo di profilatura specificato.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1468b4e7931a0a4d6f39593c28f42563cacce7952a7ab853a362fb4240e11083
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441709"
---
# <a name="start"></a>Avvio
**L'opzione** Start è *VSPerfCmd.exe'opzione* che inizializza il profiler sul metodo di profilatura specificato.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametri
 `Method` Deve essere una delle parole chiave seguenti:

- **TRACE**: specifica il metodo di strumentazione.

- **SAMPLE**: specifica il metodo di campionamento.

- **COVERAGE**: specifica il code coverage.

- **CONCURRENCY**: specifica il metodo di conflitto di risorse.

## <a name="required-options"></a>Opzioni obbligatorie
 È necessario specificare l'opzione **Output** quando nella riga di comando viene specificato **Start**.

 **Output:** `filename` Specifica il nome del file di output.

## <a name="exclusive-options"></a>Opzioni esclusive
 È possibile usare le opzioni seguenti solo con l'opzione **Start** nella riga di comando.

 **CrossSession**&#124;**CS** Abilita la profilatura tra processi. Sono supportati entrambi i nomi dell'opzione **CrossSession** e **CS**.

 **Utente:**[ `domain\` ] Abilita `username` l'accesso client al monitoraggio dall'account specificato.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** specifica un contatore delle prestazioni di Windows da includere come contrassegno nel file di dati di profilatura. **AutoMark** specifica l'intervallo in millisecondi tra le raccolte del file di dati.

## <a name="invalid-options"></a>Opzioni non valide
 Non è possibile usare le opzioni seguenti con l'opzione **Start** nella riga di comando.

 **Lo** **stato** si applica ai processi profilati. Questa opzione elenca i processi e i thread insieme al relativo stato di profilatura corrente (On/Off). Ad esempio, se un processo viene arrestato, **Status** non indica questo stato nel rapporto. **Status** mostra che il processo è profilato o non profilato.

 **Shutdown**[**:** `Timeout` ] Disattiva il profiler.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come usare *lVSPerfCmd.exe'opzione* **Start** per inizializzare il profiler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
