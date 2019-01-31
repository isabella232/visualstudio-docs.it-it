---
title: La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 37155efecd7019c0de82d37ee8b071a74a29eea6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966530"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata

Salvare la stringa di connessione nel file DBML corrente e i file di configurazione dell'applicazione con queste informazioni riservate?  Fare clic su **No** per salvare la stringa di connessione senza le informazioni riservate.

Quando si usano connessioni dati in cui sono contenute informazioni riservate, ad esempio le password incluse nella stringa di connessione, è possibile salvare la stringa di connessione nel file DBML di un progetto e il file di configurazione dell'applicazione con o senza le informazioni riservate.

> [!WARNING]
> Se si imposta in modo esplicito la proprietà **Impostazioni applicazione** presente nelle proprietà **Connessione** su **False**, la password verrà aggiunta nel file DBML.

## <a name="save-options"></a>Opzioni di salvataggio

- Per salvare la stringa di connessione con le informazioni riservate, scegliere **Sì**.

   La stringa di connessione viene archiviata come impostazione dell'applicazione e include le informazioni riservate in testo normale. Il file DBML non contiene le informazioni riservate.

- Per salvare la stringa di connessione senza le informazioni riservate, scegliere **No**.

   La stringa di connessione viene archiviata come impostazione dell'applicazione, ma non viene inclusa la password.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)