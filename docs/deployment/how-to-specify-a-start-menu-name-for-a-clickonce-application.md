---
title: Specificare il nome del menu Start per un'app ClickOnce
description: Per informazioni su come modificare il nome visualizzato per l'applicazione ClickOnce, impostare nome prodotto nella finestra di dialogo Opzioni di pubblicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12a6ebce0ff3bb7c3040765c1a82f876d0055c4d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349672"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: Specificare il nome di un'applicazione ClickOnce per il menu Start
Quando un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene installata per l'utilizzo online e offline, viene aggiunta una voce al menu **Start** e all'elenco **Installazione applicazioni** . Per impostazione predefinita, il nome visualizzato corrisponde al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato impostando **nome prodotto** nella finestra di dialogo **Opzioni di pubblicazione** .

 Il **nome del prodotto** verrà visualizzato nella pagina *publish.htm* ; per un'applicazione offline installata, sarà il nome della voce nel menu **Start** , che sarà anche il nome che viene visualizzato in **installazione** applicazioni.

 **Il nome del server di pubblicazione** verrà visualizzato nella pagina *publish.htm* sopra il **nome del prodotto** e, per un'applicazione offline installata, sarà anche il nome della cartella che contiene l'icona dell'applicazione nel menu **Start** .

 Il collegamento al menu Start o il riferimento all'app viene creato in *%AppData%\Microsoft\Windows\Start avvio\programmi \\<nome \> dell'autore*. Il collegamento o il riferimento all'app ha lo stesso nome del nome del prodotto.

 È possibile impostare le proprietà **nome prodotto** e **nome server di pubblicazione** nella finestra di dialogo **Opzioni di pubblicazione** , disponibile nella pagina **pubblica** di **Progettazione progetti**.

### <a name="to-specify-a-start-menu-name"></a>Per specificare il nome di un menu Start

1. Con un progetto selezionato in **Esplora soluzioni** , scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .

4. Fare clic su **Descrizione**.

5. Nella finestra di dialogo **Opzioni di pubblicazione** immettere il nome da visualizzare in **Product Name**.

6. Facoltativamente, è possibile immettere un nome del server di pubblicazione nel **nome dell'editore**.

## <a name="see-also"></a>Vedere anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)