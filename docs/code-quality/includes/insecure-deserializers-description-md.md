---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118152"
---
Deserializers non sicuri sono vulnerabili durante la deserializzazione di dati non attendibili. Un utente malintenzionato potrebbe modificare i dati serializzati per includere i tipi imprevisti con effetti collaterali dannosi. Un attacco contro un deserializzatore non sicuro può, ad esempio, eseguire i comandi nel sistema operativo sottostante, comunichi sulla rete o eliminare file.