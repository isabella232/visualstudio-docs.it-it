---
title: Configurare le informazioni di configurazione per una Office soluzione
description: Informazioni su come usare i file di configurazione per configurare le impostazioni specifiche per le Microsoft Office soluzioni.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1fd59fb61cf1d84c35bbcbbe406030318b8f57c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032706"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Procedura: Configurare le informazioni di configurazione per una Office soluzione
  È possibile usare i file di configurazione per configurare le impostazioni specifiche per le Office soluzioni. È possibile specificare impostazioni quali i criteri di associazione di assembly, gli oggetti remoti, le impostazioni di debug e di traccia.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Per aggiungere un file di configurazione al Office progetto

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nel riquadro **Categorie** fare clic su **Generale.**

3. Nel riquadro **Modelli** selezionare File **di configurazione dell'applicazione.**

4. Nella casella **Nome** digitare lo stesso nome dell'assembly più l'estensione *.config*. Ad esempio, un file di configurazione per un assembly Excel progetto denominato *ExcelWorkbook1.dll* verrà denominato *ExcelWorkbook1.dll.config*.

5. Fare clic su **Aggiungi**.

6. Creare il file di configurazione in base allo schema del file di configurazione dell'applicazione. Per altre informazioni, vedere [Schema del file di configurazione per .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Non esistono considerazioni speciali per l'uso dei file di configurazione con Office progetti.

## <a name="see-also"></a>Vedi anche
- [Schema del file di configurazione per .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Distribuire una Office distribuzione](../vsto/deploying-an-office-solution.md)
