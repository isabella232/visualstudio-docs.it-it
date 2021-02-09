---
title: Configurare le informazioni di configurazione per una soluzione Office
description: Informazioni su come usare i file di configurazione per configurare le impostazioni specifiche per le soluzioni Microsoft Office.
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
ms.workload:
- office
ms.openlocfilehash: da3a08ad9b3f6c78a10891e7d8ef2093ab46305d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927704"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Procedura: impostare le informazioni di configurazione per una soluzione Office
  È possibile usare i file di configurazione per configurare le impostazioni specifiche per le soluzioni Office. È possibile specificare impostazioni quali i criteri di associazione degli assembly, gli oggetti remoti, il debug e le impostazioni di traccia.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Per aggiungere un file di configurazione al progetto di Office

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Nel riquadro **categorie** fare clic su **generale**.

3. Nel riquadro **modelli** selezionare file di **configurazione dell'applicazione**.

4. Nella casella **nome** Digitare lo stesso nome dell'assembly più Extension *. config*. Ad esempio, un file di configurazione per un assembly del progetto di Excel denominato *ExcelWorkbook1.dll* verrebbe denominato *ExcelWorkbook1.dll.config*.

5. Fare clic su **Aggiungi**.

6. Creare il file di configurazione in base allo schema del file di configurazione dell'applicazione. Per ulteriori informazioni, vedere [schema dei file di configurazione per il .NET Framework](/dotnet/framework/configure-apps/file-schema/index).

   Non esistono considerazioni speciali per l'uso dei file di configurazione con i progetti di Office.

## <a name="see-also"></a>Vedi anche
- [Schema del file di configurazione per il .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
