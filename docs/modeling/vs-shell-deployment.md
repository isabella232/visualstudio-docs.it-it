---
title: Distribuzione della shell di Visual Studio
description: Scopri in che modo una shell isolata ti permette di determinare le funzionalità di Visual Studio che ti servono per interagire con il linguaggio DSL e la modalità di visualizzazione della soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1293593e71aa57d8e74b9035320b3da5108aba09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924217"
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