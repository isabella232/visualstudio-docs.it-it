---
title: 'Procedura: Introduzione alla personalizzazione della barra multifunzione'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f164a8f1d1c84725530e7a3afab5e63472ae257e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967898"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procedura: Introduzione alla personalizzazione della barra multifunzione
  Per personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un **sulla barra multifunzione (finestra di progettazione visiva)** oppure **della barra multifunzione (XML)** elemento a un progetto di Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Per aggiungere una barra multifunzione a un progetto

1. Nel **Project** Menu, fare clic su **Aggiungi nuovo elemento**.

2. Nel **Aggiungi nuovo elemento** finestra di dialogo **della barra multifunzione (finestra di progettazione visiva)** oppure **sulla barra multifunzione (XML)**. Per altre informazioni su tali modelli, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).

3. Nel **nome** , digitare un nome per l'elemento della barra multifunzione.

    I nomi non possono contenere i caratteri seguenti:

   - Cancelletto (#)

   - Simbolo di percentuale (%)

   - Ampersand (&)

   - Asterisco (*)

   - Barra verticale (|)

   - Barra rovesciata (\\)

   - Due punti (:)

   - Virgolette doppie (")

   - Minore di (\<)

   - Maggiore di (>)

   - Punto interrogativo (?)

   - Barra (/)

   - Spazi iniziali o finali (' ')

   - Nomi riservati di Windows o DOS, ad esempio ("nul", "aux", "con", "com1", "lpt1" e così via)

4. Fare clic su **OK**.

   L'elemento della barra multifunzione viene visualizzato nella **Esplora soluzioni**. Per informazioni sui passaggi successivi, vedere [Panoramica della barra multifunzione](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
