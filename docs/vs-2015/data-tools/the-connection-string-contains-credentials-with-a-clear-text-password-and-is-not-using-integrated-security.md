---
title: La stringa di connessione contiene credenziali con una password in testo non crittografato e non usa la sicurezza integrata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 82a76f36f3b7cf0f4687d8797fe2694b731933ca
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666923"
---
# <a name="the-connection-string-contains-credentials-with-a-clear-text-password-and-is-not-using-integrated-security"></a>La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Salvare la stringa di connessione nel file DBML corrente e i file di configurazione dell'applicazione con queste informazioni riservate?  Fare clic su No per salvare la stringa di connessione senza le informazioni riservate.  
  
 Quando si usano connessioni dati in cui sono contenute informazioni riservate, ad esempio le password incluse nella stringa di connessione, è possibile salvare la stringa di connessione nel file DBML di un progetto e il file di configurazione dell'applicazione con o senza le informazioni riservate.  
  
> [!WARNING]
>  Se si imposta in modo esplicito la proprietà **Impostazioni applicazione** presente nelle proprietà **Connessione** su **False**, la password verrà aggiunta nel file DBML.  
  
### <a name="to-save-the-connection-string-with-the-sensitive-information-in-the-projects-application-settings"></a>Per salvare la stringa di connessione con le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Scegliere **Sì**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione e include le informazioni riservate in testo normale. Il file DBML non contiene le informazioni riservate.  
  
### <a name="to-save-the-connection-string-without-the-sensitive-information-in-the-projects-application-settings"></a>Per salvare la stringa di connessione senza le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Fare clic su **No**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione, ma non viene inclusa la password.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
