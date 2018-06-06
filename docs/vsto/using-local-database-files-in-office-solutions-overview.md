---
title: Utilizzare i file di database locale in panoramica di soluzioni Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01e9dc3df93e1f721eba9ce3bcf65d4fb8bb1ca1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767582"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Utilizzare i file di database locale in panoramica di soluzioni Office
  È possibile includere un file di database, ad esempio SQL Server Express (*file con estensione mdf*) file o Microsoft Office Access (*mdb*) file nella soluzione Office. Ciò consente agli utenti finali di gestire un database locale nelle situazioni in cui la gestione di un database centralizzato non necessarie, ad esempio in una soluzione locale di inventario che viene utilizzata solo un singolo computer.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Importare il file di database in un progetto  
 Per importare il file di database al progetto, utilizzare il **configurazione guidata origine dati** per creare un'origine dati in base al file di database. La procedura guidata aggiunge il file di database e un dataset tipizzato al progetto.  
  
## <a name="deploy-the-database-file"></a>Distribuire il file di database  
 Il **configurazione guidata origine dati** utilizza un percorso relativo per creare connessioni al file di database locale. In questo modo è possibile copiare la soluzione da un computer a un altro, se si gestiscono i percorsi relativi dei file.  
  
 Se si distribuisce la soluzione a un server e quindi distribuire il documento per ogni utente finale, è necessario distribuire il file di database manualmente e installarlo nella stessa posizione relativo al documento. Ciò significa che l'utente finale non è possibile spostare il documento in una nuova posizione nel proprio computer, a meno che non si anche sposta il file di database.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>File di database locali e la memorizzazione nella cache il set di dati  
 Nelle soluzioni a livello di documento per Microsoft Office Excel e Microsoft Office Word, è possibile memorizzare nella cache set di dati nel documento contrassegnando l'istanza del set di dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Quando si aggiunge il file di database al progetto utilizzando il **configurazione guidata origine dati**, un dataset tipizzato viene aggiunto automaticamente al progetto. Raramente è necessario applicare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> per questo set di dati, poiché i dati sono già locali nel computer dell'utente. Per altre informazioni, vedere [memorizzare nella Cache dati](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: aggiornare un'origine dati con i dati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Dati nella cache](../vsto/caching-data.md)  
  
  