---
title: Distribuzione della shell di Visual Studio
description: Scopri in che modo una shell isolata ti permette di determinare le funzionalità di Visual Studio che ti servono per interagire con il linguaggio DSL e la modalità di visualizzazione della soluzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361261"
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