---
title: 'Procedura: Iniziare a personalizzare la barra multifunzione'
description: Informazioni su come personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento Barra multifunzione (finestra di progettazione visiva) o Barra multifunzione (XML) a un Office progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f4042a8d68ac940df8e84ac62fb85b902879e1ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083466"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procedura: Iniziare a personalizzare la barra multifunzione
  Per personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento Barra multifunzione **(finestra** di progettazione visiva) o Barra **multifunzione (XML)** a un Office progetto.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Per aggiungere una barra multifunzione a un progetto

1. Nel menu **Project** fare clic **su Aggiungi nuovo elemento**.

2. Nella finestra **di dialogo Aggiungi nuovo elemento** selezionare Barra multifunzione **(finestra di progettazione visiva)** o **Barra multifunzione (XML).** Per altre informazioni su questi modelli, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

3. Nella casella **Nome** digitare un nome per l'elemento della barra multifunzione.

    I nomi non possono includere i caratteri seguenti:

   - Cancelletto (#)

   - Percentuale (%)

   - E commerciale (&)

   - Asterisco (*)

   - Barra verticale {|}

   - Barra rovesciata (\\)

   - Due punti (:)

   - Virgolette doppie (")

   - Minore di (\<)

   - Maggiore di (>)

   - Punto interrogativo (?)

   - Barra (/)

   - Spazi iniziali o finali (' ')

   - Nomi riservati per Windows o DOS, ad esempio ("nul", "aux", "con", "com1", "lpt1" e così via)

4. Fare clic su **OK**.

   L'elemento barra multifunzione viene visualizzato **in Esplora soluzioni**. Per informazioni sui passaggi successivi, vedere Panoramica [della barra multifunzione.](../vsto/ribbon-overview.md)

## <a name="see-also"></a>Vedi anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando xml della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
