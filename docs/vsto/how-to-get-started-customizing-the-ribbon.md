---
title: 'Procedura: iniziare a personalizzare la barra multifunzione'
description: Informazioni su come personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento barra multifunzione (finestra di progettazione visiva) o barra multifunzione (XML) a un progetto di Office.
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
ms.workload:
- office
ms.openlocfilehash: d82d059166b9efbb80ed6ce4cffcbb973235b01b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953916"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procedura: iniziare a personalizzare la barra multifunzione
  Per personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento **barra multifunzione (finestra di progettazione visiva)** o **barra multifunzione (XML)** a un progetto di Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Per aggiungere una barra multifunzione a un progetto

1. Scegliere **Aggiungi nuovo elemento** dal menu **progetto** .

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **barra multifunzione (finestra di progettazione visiva)** o **barra multifunzione (XML)**. Per ulteriori informazioni su questi modelli, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

3. Nella casella **nome** Digitare un nome per l'elemento della barra multifunzione.

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

   - Nomi riservati per Windows o DOS, ad esempio ("NUL", "aux", "con", "COM1", "LPT1" e così via)

4. Fare clic su **OK**.

   L'elemento della barra multifunzione viene visualizzato in **Esplora soluzioni**. Per informazioni sui passaggi successivi, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Vedi anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
