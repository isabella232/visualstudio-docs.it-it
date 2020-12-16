---
title: 'Procedura: recuperare una cartella per nome a livello di codice'
description: Informazioni su come usare Visual Studio per recuperare a livello di codice una cartella in base al nome e quindi visualizzare il contenuto della cartella.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], retrieving by name
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4e615897fedcbfa41ad7958e93354718d9ccfbc
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528577"
---
# <a name="how-to-programmatically-retrieve-a-folder-by-name"></a>Procedura: recuperare una cartella per nome a livello di codice
  Questo esempio Mostra come ottenere un riferimento a una cartella personalizzata denominata e quindi visualizzare il contenuto della cartella.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_GetFolderName#1](../vsto/codesnippet/CSharp/Trin_OL_GetFolderName/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Cartella denominata TestFolder.

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Procedura: eseguire una ricerca all'interno di una cartella specifica a livello di codice](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Procedura: eseguire la ricerca di un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Procedura: creare elementi di cartelle personalizzate a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md)
