---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f3729c09198b331728e2cc67299ffc3ad6c3d26
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809648"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare le funzionalità di Visual Studio necessarie per interagire con il linguaggio specifico di dominio e la modalità di visualizzazione della soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della shell isolata](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).

Per impostare una shell di Visual Studio come destinazione della distribuzione:

1. Nel progetto **DslPackage** aprire **source.Extension.TT**.

2. In `<SupportedProducts>` Inserisci:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Sostituire *MyIsolatedShell* con il nome del pacchetto della shell isolata.