---
title: 'Procedura: Riabilitare un VSTO Add-in è stato disabilitato'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 85a3ba42f4e22016f487e4a4024e4cfd6736be06
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617496"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Procedura: Riabilitare un VSTO Add-in è stato disabilitato
  Le applicazioni di Microsoft Office possono disabilitare i componenti aggiuntivi VSTO che si comportano in modo imprevisto. Se un'applicazione non carica un componente aggiuntivo VSTO quando si tenta di eseguirne il debug, il componente aggiuntivo VSTO potrebbe essere stato disabilitato dall'applicazione in seguito alla chiusura dell'applicazione (disabilitazione di tipo "hard") o a un errore del componente (disabilitazione di tipo "soft").

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Componenti aggiuntivi VSTO con disabilitazione di disco rigido
 La disabilitazione hard può verificarsi quando un componente aggiuntivo VSTO causa la chiusura imprevista dell'applicazione. Si potrebbe verificare anche nel computer di sviluppo se si arresta il debugger durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> nel componente aggiuntivo VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Per riabilitare un componente aggiuntivo VSTO

1.  Nell'applicazione fare clic sulla scheda **File** .

2.  Scegliere il *NomeApplicazione* **opzioni** pulsante.

3.  Nel riquadro delle categorie fare clic su **Componenti aggiuntivi**.

4.  Nel riquadro dei dettagli verificare che il componente aggiuntivo VSTO sia visualizzato nell'elenco **Componenti aggiuntivi di applicazioni disattivati** .

     La colonna **Nome** specifica il nome dell'assembly e la colonna **Percorso** specifica il percorso completo del manifesto dell'applicazione.

5.  Nella casella **Gestione** fare clic su **Elementi disattivati**e quindi su **Vai**.

6.  Selezionare il componente aggiuntivo VSTO e fare clic su **Attiva**.

7.  Fare clic su **Chiudi**.

## <a name="soft-disabled-vsto-add-ins"></a>Componenti aggiuntivi VSTO con disabilitazione soft
 La disabilitazione di tipo "soft" può verificarsi quando un componente aggiuntivo VSTO genera un errore che non causa la chiusura imprevista dell'applicazione. Ad esempio, un'applicazione potrebbe eseguire la disabilitazione di tipo "soft" di un componente aggiuntivo VSTO se viene generata un'eccezione non gestita durante l'esecuzione del gestore eventi <xref:Microsoft.Office.Tools.AddIn.Startup> .

> [!NOTE]
>  Quando si riabilita un componente aggiuntivo VSTO dopo la disabilitazione di tipo "soft", l'applicazione tenta immediatamente di caricare il componente aggiuntivo VSTO. Se il problema che ha inizialmente causato la disabilitazione di tipo "soft" del componente aggiuntivo VSTO non è stato risolto, l'applicazione ne eseguirà di nuovo la disabilitazione di tipo "soft".

### <a name="to-re-enable-a-vsto-add-in"></a>Per riabilitare un componente aggiuntivo VSTO

1.  Nell'applicazione fare clic sulla scheda **File** .

2.  Scegliere il *NomeApplicazione* **opzioni** pulsante.

3.  Nel riquadro delle categorie fare clic su **Componenti aggiuntivi**.

4.  Nel riquadro dei dettagli verificare che il componente aggiuntivo VSTO sia visualizzato nell'elenco **Componenti aggiuntivi di applicazioni inattivi** .

     La colonna **Nome** specifica il nome dell'assembly e la colonna **Percorso** specifica il percorso completo del manifesto dell'applicazione.

5.  Nella casella **Gestione** fare clic su **Componenti aggiuntivi COM**e quindi su **Vai**.

6.  Nella finestra di dialogo **Componenti aggiuntivi COM** selezionare la casella di controllo accanto al componente aggiuntivo VSTO disabilitato.

7.  Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
- [Creazione di soluzioni Office](../vsto/building-office-solutions.md)
- [Eseguire il debug di progetti di Office](../vsto/debugging-office-projects.md)
- [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)
