---
title: 'Procedura: Abilitare nuovamente un componente VSTO componente aggiuntivo disabilitato'
description: Informazioni su come usare Visual Studio per abilitare nuovamente un componente aggiuntivo VSTO che è stato disabilitato in un'Microsoft Office applicazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ecaca6e262113ae4926ff21af5c468703fe78ae9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025979"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Procedura: Abilitare nuovamente un componente VSTO componente aggiuntivo disabilitato
  Le applicazioni di Microsoft Office possono disabilitare i componenti aggiuntivi VSTO che si comportano in modo imprevisto. Se un'applicazione non carica un componente aggiuntivo VSTO quando si tenta di eseguirne il debug, il componente aggiuntivo VSTO potrebbe essere stato disabilitato dall'applicazione in seguito alla chiusura dell'applicazione (disabilitazione di tipo "hard") o a un errore del componente (disabilitazione di tipo "soft").

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Componenti aggiuntivi VSTO disabilitati
 La disabilitazione rigida può verificarsi quando VSTO componente aggiuntivo causa la chiusura imprevista dell'applicazione. Si potrebbe verificare anche nel computer di sviluppo se si arresta il debugger durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> nel componente aggiuntivo VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Per riabilitare un componente aggiuntivo VSTO

1. Nell'applicazione fare clic sulla scheda **File** .

2. Fare clic *sul pulsante ApplicationName* **Options (Opzioni nome** applicazione).

3. Nel riquadro delle categorie fare clic su **Componenti aggiuntivi**.

4. Nel riquadro dei dettagli verificare che il componente aggiuntivo VSTO sia visualizzato nell'elenco **Componenti aggiuntivi di applicazioni disattivati** .

     La colonna **Nome** specifica il nome dell'assembly e la colonna **Percorso** specifica il percorso completo del manifesto dell'applicazione.

5. Nella casella **Gestione** fare clic su **Elementi disattivati** e quindi su **Vai**.

6. Selezionare il componente aggiuntivo VSTO e fare clic su **Attiva**.

7. Fare clic su **Chiudi**.

## <a name="soft-disabled-vsto-add-ins"></a>Componenti aggiuntivi VSTO disabilitati
 La disabilitazione di tipo "soft" può verificarsi quando un componente aggiuntivo VSTO genera un errore che non causa la chiusura imprevista dell'applicazione. Ad esempio, un'applicazione potrebbe eseguire la disabilitazione di tipo "soft" di un componente aggiuntivo VSTO se viene generata un'eccezione non gestita durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> .

> [!NOTE]
> Quando si riabilita un componente aggiuntivo VSTO dopo la disabilitazione di tipo "soft", l'applicazione tenta immediatamente di caricare il componente aggiuntivo VSTO. Se il problema che ha inizialmente causato la disabilitazione di tipo "soft" del componente aggiuntivo VSTO non è stato risolto, l'applicazione ne eseguirà di nuovo la disabilitazione di tipo "soft".

### <a name="to-re-enable-a-vsto-add-in"></a>Per riabilitare un componente aggiuntivo VSTO

1. Nell'applicazione fare clic sulla scheda **File** .

2. Fare clic *sul pulsante ApplicationName* **Options (Opzioni nome** applicazione).

3. Nel riquadro delle categorie fare clic su **Componenti aggiuntivi**.

4. Nel riquadro dei dettagli verificare che il componente aggiuntivo VSTO sia visualizzato nell'elenco **Componenti aggiuntivi di applicazioni inattivi** .

     La colonna **Nome** specifica il nome dell'assembly e la colonna **Percorso** specifica il percorso completo del manifesto dell'applicazione.

5. Nella casella **Gestione** fare clic su **Componenti aggiuntivi COM** e quindi su **Vai**.

6. Nella finestra di dialogo **Componenti aggiuntivi COM** selezionare la casella di controllo accanto al componente aggiuntivo VSTO disabilitato.

7. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche
- [Compilare Office soluzioni](../vsto/building-office-solutions.md)
- [Eseguire il debug Office progetti](../vsto/debugging-office-projects.md)
- [Componenti aggiuntivi VSTO programma](../vsto/programming-vsto-add-ins.md)
