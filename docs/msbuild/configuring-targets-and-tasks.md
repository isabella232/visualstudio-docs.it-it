---
title: Configurazione di destinazioni e attività | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634396"
---
# <a name="configure-targets-and-tasks"></a>Configurare destinazioni e attività

È possibile configurare le destinazioni e le attività di MSBuild per l'esecuzione out-of-process con MSBuild, in modo che sia possibile specificare come destinazione contesti che differiscono da quello corrente in cui è in esecuzione l'applicazione. Ad esempio, è possibile specificare come destinazione un'applicazione .NET Framework 2.0 a 32 bit mentre nel computer di sviluppo è in esecuzione un sistema operativo .NET Framework 4.5 a 64 bit. Inoltre, è possibile specificare come destinazione computer in cui viene eseguito .NET Framework 4 o versione precedente. La combinazione tra 32 o 64 bit e la versione specifica di .NET Framework viene definita *contesto di destinazione*.

## <a name="installation"></a>Installazione

  Se si vuole installare MSBuild separatamente da Visual Studio, è possibile scaricare il pacchetto di installazione dal [download di MSBuild](https://www.microsoft.com/download/details.aspx?id=40760). È inoltre necessario installare le versioni di .NET Framework che si prevede di usare.

## <a name="targets-and-tasks"></a>Destinazioni e attività

 In MSBuild vengono eseguite alcune attività di compilazione out-of-process per specificare come destinazione un set più ampio di contesti.  Ad esempio, in un'istanza di MSBuild a 32 bit è possibile eseguire un'attività di compilazione in un processo a 64 bit destinato a un computer a 64 bit. Questa funzionalità è controllata dagli argomenti `UsingTask` e dai parametri `Task`. Questi argomenti e parametri vengono impostati dalle destinazioni installate da .NET Framework 4.5 e non è necessaria alcuna modifica per compilare applicazioni per i vari contesti di destinazione.

 Se si desidera creare un contesto di destinazione personalizzato, è necessario impostare questi argomenti e parametri in modo appropriato. Per gli esempi, vedere il file .NET Framework 4,5 *Microsoft. Common. targets* e il file *Microsoft. Common. Tasks* .  Per informazioni su come creare un'attività personalizzata che può funzionare con più contesti di destinazione o come modificare le attività esistenti, vedere [procedura: configurare destinazioni e attività](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Vedere anche

- [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)
