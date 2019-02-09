---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70f39dd23851a2ebc0a48afd05da54b0d8deb24a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955674"
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