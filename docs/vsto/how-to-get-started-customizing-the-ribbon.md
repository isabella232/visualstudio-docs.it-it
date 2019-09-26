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
ms.openlocfilehash: a9b0f1ef704f5dd1426374e23806e5950ed5f6bb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255866"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Procedura: Introduzione alla personalizzazione della barra multifunzione
  Per personalizzare la barra multifunzione di un'applicazione Microsoft Office, aggiungere un elemento **barra multifunzione (finestra di progettazione visiva)** o **barra multifunzione (XML)** a un progetto di Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Per aggiungere una barra multifunzione a un progetto

1. Scegliere **Aggiungi nuovo elemento**dal menu **progetto** .

2. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **barra multifunzione (finestra di progettazione visiva)** o **barra multifunzione (XML)** . Per ulteriori informazioni su questi modelli, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

3. Nella casella **nome** Digitare un nome per l'elemento della barra multifunzione.

    I nomi non possono contenere i caratteri seguenti:

   - Sterlina (#)

   - Percentuale (%)

   - E commerciale (&)

   - Asterisco (*)

   - Barra verticale (|)

   - Barra rovesciata (\\)

   - Due punti (:)

   - Virgolette doppie (")

   - Minore di (\<)

   - Maggiore di (>)

   - Punto interrogativo (?)

   - Barra (/)

   - Spazi iniziali o finali ('')

   - Nomi riservati per Windows o DOS, ad esempio ("NUL", "aux", "con", "COM1", "LPT1" e così via)

4. Fare clic su **OK**.

   L'elemento della barra multifunzione viene visualizzato in **Esplora soluzioni**. Per informazioni sui passaggi successivi, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Vedere anche
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
