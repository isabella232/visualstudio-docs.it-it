---
title: Distribuzione di VS shell | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659310"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una shell isolata consente di determinare le funzionalità di Visual Studio necessarie per interagire con il linguaggio specifico di dominio e la modalità di visualizzazione della soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della shell isolata](../extensibility/customizing-the-isolated-shell.md). È possibile trovare altre informazioni su come personalizzare la shell isolata in [personalizzazione della shell isolata](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf).

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Per impostare una shell di Visual Studio come destinazione della distribuzione

1. Nel progetto **DslPackage** aprire **source.Extension.TT**.

2. In `<SupportedProducts>` Inserisci:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Sostituire *MyIsolatedShell* con il nome del pacchetto della shell isolata.
