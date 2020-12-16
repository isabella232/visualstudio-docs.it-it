---
title: Panoramica sull'uso dei file di database locali nelle soluzioni Office
description: Informazioni su come includere un file di database, ad esempio un file di SQL Server Express (con estensione MDF) o un file con estensione mdb (Microsoft Office Access) nella soluzione Office.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1a3166a88080eaee1042187c171c4938d236058a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526559"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Panoramica sull'uso dei file di database locali nelle soluzioni Office
  È possibile includere un file di database, ad esempio un file di SQL Server Express (con *estensione MDF*) o un file con estensione *MDB*(Microsoft Office Access) nella soluzione Office. Ciò consente agli utenti finali di gestire un database locale in situazioni in cui la gestione di un database centralizzato non è necessaria, ad esempio in una soluzione di inventario locale utilizzata su un solo computer.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importare il file di database in un progetto
 Per importare il file di database nel progetto, utilizzare la **Configurazione guidata origine dati** per creare un'origine dati basata sul file di database. La procedura guidata aggiunge il file di database e un set di dati tipizzato al progetto.

## <a name="deploy-the-database-file"></a>Distribuire il file di database
 La **Configurazione guidata origine dati** utilizza un percorso relativo per creare connessioni al file di database locale. In questo modo è possibile copiare la soluzione da un computer a un altro se si gestiscono le posizioni relative dei file.

 Se si distribuisce la soluzione in un server e quindi si distribuisce il documento a ogni utente finale, è inoltre necessario distribuire manualmente il file di database e installarlo nella stessa posizione relativa al documento. Ciò significa che l'utente finale non può spostare il documento in una nuova posizione nel suo computer, a meno che non sposti anche il file di database.

## <a name="local-database-files-and-caching-the-dataset"></a>File di database locali e memorizzazione nella cache del set di dati
 Nelle soluzioni a livello di documento per Microsoft Office Excel e Microsoft Office Word, è possibile memorizzare nella cache i set di dati nel documento contrassegnando l'istanza del set di dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . Quando si aggiunge il file di database al progetto tramite la **Configurazione guidata origine dati**, un set di dati tipizzato viene aggiunto automaticamente al progetto. Raramente è necessario applicarlo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> a questo set di dati, perché i dati sono già locali nel computer dell'utente. Per altre informazioni, vedere [memorizzare i dati nella cache](../vsto/caching-data.md).

## <a name="see-also"></a>Vedere anche
- [Associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: aggiornare un'origine dati con i dati di un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Dati cache](../vsto/caching-data.md)
