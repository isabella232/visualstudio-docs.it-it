---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541568"
---
Deserializers non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere i tipi imprevisti con effetti collaterali dannosi. Un attacco contro un deserializzatore non sicuro può, ad esempio, eseguire i comandi nel sistema operativo sottostante, comunichi sulla rete o eliminare file.