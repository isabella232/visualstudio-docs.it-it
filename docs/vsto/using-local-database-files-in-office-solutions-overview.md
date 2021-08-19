---
title: Usare i file di database locali nella Office delle soluzioni
description: Informazioni su come includere un file di database, ad esempio un file SQL Server Express (con estensione mdf) o un file di Microsoft Office Access (con estensione mdb), nella soluzione Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f2e7dc3346ccb2104e5350968d2f983b1c2e1c69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099425"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Usare i file di database locali nella Office delle soluzioni
  È possibile includere un file di database, ad esempio un file SQL Server Express (*mdf*) o un file di Microsoft Office Access *(mdb),* nella soluzione Office. Ciò consente agli utenti finali di gestire un database locale in situazioni in cui la gestione di un database centralizzato non è necessaria, ad esempio in una soluzione di inventario locale usata in un solo computer.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importare il file di database in un progetto
 Per importare il file di database nel progetto, usare la **Configurazione** guidata origine dati per creare un'origine dati basata sul file di database. La procedura guidata aggiunge il file di database e un set di dati tipizzato al progetto.

## <a name="deploy-the-database-file"></a>Distribuire il file di database
 La **Configurazione guidata origine dati usa** un percorso relativo per creare connessioni al file di database locale. In questo modo è possibile copiare la soluzione da un computer a un altro se si mantengono le posizioni relative dei file.

 Se si distribuisce la soluzione in un server e quindi si distribuisce il documento a ogni utente finale, è necessario distribuire manualmente il file di database e installarlo nella stessa posizione relativa al documento. Ciò significa che l'utente finale non può spostare il documento in una nuova posizione nel computer, a meno che non sposti anche il file di database.

## <a name="local-database-files-and-caching-the-dataset"></a>File di database locali e memorizzazione nella cache del set di dati
 Nelle soluzioni a livello di documento per Microsoft Office Excel e Microsoft Office Word, è possibile memorizzare nella cache i set di dati nel documento contrassegnando l'istanza del set di dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Quando si aggiunge il file di database al progetto tramite la Configurazione guidata origine **dati,** al progetto viene aggiunto automaticamente un set di dati tipizzato. Raramente è necessario applicare a questo set di <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> dati, perché i dati sono già locali nel computer dell'utente. Per altre informazioni, vedere [Memorizzare nella cache i dati](../vsto/caching-data.md).

## <a name="see-also"></a>Vedi anche
- [Associare dati ai controlli in Office soluzioni](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
- [Dati cache](../vsto/caching-data.md)
