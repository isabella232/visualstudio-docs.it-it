---
title: Usare i file di database locale in panoramica di soluzioni Office
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
ms.openlocfilehash: ea260a6286c8a923d56ab7a5088b55de57004489
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645537"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Usare i file di database locale in panoramica di soluzioni Office
  È possibile includere un file di database, ad esempio SQL Server Express (*mdf*) file o Microsoft Office Access (*mdb*) file, nella soluzione Office. Ciò consente agli utenti di gestire un database locale nelle situazioni in cui la gestione di un database centralizzato non necessaria, ad esempio in una soluzione locale di inventario che viene usata solo un singolo computer.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Importare il file di database in un progetto
 Per importare il file di database nel progetto, usare il **configurazione guidata origine dati** per creare un'origine dati basata sul file di database. La procedura guidata aggiunge i file di database e un set di dati tipizzato al progetto.

## <a name="deploy-the-database-file"></a>Distribuire il file di database
 Il **configurazione guidata origine dati** Usa un percorso relativo per creare connessioni a file di database locale. In questo modo è possibile copiare la soluzione da un computer a un altro, se si gestiscono i percorsi relativi dei file.

 Se si distribuisce la soluzione in un server e quindi distribuire il documento per ogni utente finale, è necessario distribuire il file di database manualmente e installarlo nella stessa posizione rispetto al documento. Ciò significa che l'utente finale non è possibile spostare il documento in una nuova posizione sul proprio computer, a meno che non si anche sposta il file di database.

## <a name="local-database-files-and-caching-the-dataset"></a>File di database locali e la memorizzazione nella cache il set di dati
 Nelle soluzioni a livello di documento per Microsoft Office Excel e Microsoft Office Word, è possibile memorizzare nella cache set di dati del documento per contrassegnare l'istanza del set di dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Quando si aggiunge il file di database al progetto usando il **configurazione guidata origine dati**, un dataset tipizzato viene aggiunto automaticamente al progetto. È raramente la necessità di applicare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> al set di dati, perché i dati sono già locali nel computer dell'utente. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).

## <a name="see-also"></a>Vedere anche
- [Associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Procedura: Popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Procedura: Aggiornare un'origine dati con dati provenienti da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Dati della cache](../vsto/caching-data.md)
