---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bc86574b380e0a29042dcc1dc20851258c9f1bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033570"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare quali Visual Studio la funzionalità è necessario interagire con il linguaggio specifico di dominio e l'aspetto di tale soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della Shell isolata](https://vspartner.com/pages/vsshells).

Per impostare una Shell di Visual Studio come destinazione di distribuzione:

1. Nel **DslPackage** progetto aprire **source.extension.tt**.

2. In `<SupportedProducts>` inserire:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Sostituire *MyIsolatedShell* con il nome del pacchetto shell isolata.