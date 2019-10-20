---
title: Distribuzione della shell di Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e010d2efd8174f2c61d7c97eb63d585f47812ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663668"
---
# <a name="vs-shell-deployment"></a>Distribuzione della shell di Visual Studio

Una shell isolata consente di determinare le funzionalità di Visual Studio necessarie per interagire con il linguaggio specifico di dominio e la modalità di visualizzazione della soluzione. Per altre informazioni sulla shell isolata di Visual Studio, vedere [personalizzazione della shell isolata](https://vspartner.com/pages/vsshells).

Per impostare una shell di Visual Studio come destinazione della distribuzione:

1. Nel progetto **DslPackage** aprire **source.Extension.TT**.

2. In `<SupportedProducts>` Inserisci:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Sostituire *MyIsolatedShell* con il nome del pacchetto della shell isolata.