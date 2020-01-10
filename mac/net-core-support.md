---
title: Supporto di .NET Core
description: Questo documento illustra il supporto delle versioni di .NET Core in Visual Studio per Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 6a4bc5a68a17bf3562e0f82b1f2c521f9b3f3e72
ms.sourcegitcommit: d04441e3c5f2eff3a63f7aca35ccf7ecac90fb44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75735805"
---
# <a name="net-core-support"></a>Supporto di .NET Core

La tabella seguente descrive le versioni di .NET Core supportate dalle versioni stabili e di anteprima di Visual Studio per Mac:

| Versione di .NET Core SDK |Visual Studio per Mac 8.1 (stabile) | Visual Studio per Mac 8.2 (stabile) | Visual Studio per Mac 8,3 (stabile) | Visual Studio per Mac 8,4 (stabile)
|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|
|v3.1 | | | |✔︎|

> [!IMPORTANT]
> Le versioni di anteprima della .NET Core SDK non sono supportate. eseguire l'aggiornamento alla versione rilasciata. Quando si installa Visual Studio per Mac 8,4, verrà installata la versione rilasciata di .NET Core v 3.1.

> [!IMPORTANT]
> Se in precedenza si usava .NET Core v2.2.1xx con Visual Studio per Mac 8.0, è necessario eseguire manualmente l'aggiornamento a una versione supportata di .NET Core, come elencato nella tabella precedente. È consigliabile eseguire l'aggiornamento alla versione [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) o [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2).

* .NET Core v 3.1 viene installato per impostazione predefinita per 8,4.
* .NET Core v 3.0 viene installato per impostazione predefinita per 8,3.
* .NET Core v2.1.701 (v2.1.700 per 8.1) viene installato per impostazione predefinita con il programma di installazione.
* Per scaricare qualsiasi altra versione di .NET Core, visitare la [pagina di dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* Quando si usa .NET Core 3,0 C# , per impostazione predefinita verrà usata la versione 8. C#7,3 è il valore predefinito quando si usa .NET Core 2. x. Per altre informazioni, vedere [ C# controllo delle versioni della lingua](/dotnet/csharp/language-reference/configure-language-version) .
* Per informazioni sull'installazione di una versione di anteprima di Visual Studio per Mac, vedere la guida [Installare un'anteprima o un aggiornamento per Visual Studio per Mac](/visualstudio/mac/install-preview).
