---
title: Supporto di .NET Core
description: Questo documento illustra il supporto delle versioni di .NET Core in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: a04d15fc2fc768c2d6896396df5dc0f134d1720b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709998"
---
# <a name="net-core-support"></a>Supporto di .NET Core

La tabella seguente descrive le versioni di .NET Core supportate dalle versioni stabili e di anteprima di Visual Studio per Mac:

| Versione di .NET Core SDK |Visual Studio per Mac 8.1 | Visual Studio per Mac 8.2 | Visual Studio per Mac 8.3 | Visual Studio per Mac 8.4 | Visual Studio per Mac 8.5 | Visual Studio per Mac 8.6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|v5.0 | | | | | |✔︎|

> [!IMPORTANT]
> Le versioni di anteprima .NET Core SDK non sono supportate. eseguire l'aggiornamento alla versione rilasciata. Quando si installa Visual Studio per Mac 8.4, verrà installata la versione rilasciata di .NET Core v3.1.

> [!IMPORTANT]
> Se in precedenza si usava .NET Core v2.2.1xx con Visual Studio per Mac 8.0, è necessario eseguire manualmente l'aggiornamento a una versione supportata di .NET Core, come elencato nella tabella precedente. È consigliabile [usare 2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) o [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2)

* .NET Core v3.1 viene installato per impostazione predefinita per 8.4, 8.5 e 8.6.
* .NET Core v3.0 viene installato per impostazione predefinita per la versione 8.3.
* .NET Core v2.1.701 (v2.1.700 per 8.1) viene installato per impostazione predefinita con il programma di installazione.
* Per scaricare qualsiasi altra versione di .NET Core, visitare la [pagina di dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* Quando si usa .NET Core 3.0, per impostazione predefinita verrà usato C# versione 8. C# 7.3 è l'impostazione predefinita quando si usa .NET Core 2.x. Per [altre informazioni, vedere Controllo delle versioni](/dotnet/csharp/language-reference/configure-language-version) del linguaggio C#.
* Per informazioni sull'installazione di una versione di anteprima di Visual Studio per Mac, vedere la guida [Installare un'anteprima o un aggiornamento per Visual Studio per Mac](./install-preview.md).