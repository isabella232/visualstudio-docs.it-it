---
title: GC (VSPerfCmd) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e14fef1cfdc2dfc5f0d737ac09a08d90ab1de309
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776979"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
L'opzione **GC** abilita la raccolta dei dati di allocazione della memoria e dei dati di durata degli oggetti di .NET Framework. L'opzione **GC** può essere usata solo con il metodo di profilatura del campionamento e solo con l'opzione **Launch**.

 Quando si usa l'opzione **GC** il comando **/sampleon** di VSPerfClrEnv non è necessario.

 Se non vengono specificati parametri o viene specificato il parametro **Allocation**, vengono raccolti solo i dati di allocazione della memoria di .NET Framework. Se viene specificato il parametro **Lifetime**, vengono raccolti sia i dati di allocazione della memoria di .NET Framework sia i dati di durata degli oggetti di .NET Framework.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametri
 **Allocation** Impostazione predefinita. Raccoglie i dati di allocazione della memoria di .NET Framework.

 **Lifetime** Raccoglie sia i dati di allocazione della memoria di .NET Framework, sia i dati di durata degli oggetti di .NET Framework.

## <a name="required-options"></a>Opzioni obbligatorie
 L'opzione **GC** può essere usata solo con l'opzione **Launch**.

 **Launch:** `AppName` avvia l'applicazione specificata e inizia la profilatura con il metodo di campionamento.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene avviata un'applicazione e vengono raccolti i dati di allocazione della memoria di .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
