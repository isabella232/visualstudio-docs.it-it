---
title: Ruoli di amministratore con privilegi super e di amministratore per Visual Studio sottoscrizione
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 03/19/2021
ms.topic: conceptual
description: Informazioni sui ruoli di amministratore con privilegi super e amministratore e su come assegnare gli amministratori.
ms.openlocfilehash: c5997004f50b78ba8484be51f3e5dd5a22aa868e
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123965588"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Amministratori con privilegi super e amministratori per i contratti Visual Studio sottoscrizione

Esistono due diversi ruoli nel nuovo portale di amministrazione delle sottoscrizioni di Visual Studio per i clienti con contratti multilicenza. Questi ruoli sono, ad esempio, il ruolo di contatto principale/per le comunicazioni e il ruolo di gestione delle sottoscrizioni che esisteva già in VLSC.

**Amministratori con privilegi super:** Quando un'organizzazione viene inizialmente impostata, il contatto principale o per le comunicazioni diventa un amministratore con privilegi per impostazione predefinita. Il contatto principale o per le comunicazioni può scegliere di assegnare altri amministratori con privilegi super o amministratori. Un amministratore con privilegi super può aggiungere e rimuovere altri amministratori e sottoscrittori. Se nel sistema sono presenti più di due amministratori con privilegi elevati, è possibile eliminarli tutti tranne gli ultimi due per motivi di sicurezza.

**Amministratori:** Un amministratore può essere assegnato solo da un amministratore con privilegi super. Un amministratore può gestire solo i sottoscrittori nei contratti assegnati dall'amministratore con privilegi più privilegi.

Guardare una dimostrazione su come gestire gli amministratori. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>Assegnazione di amministratori
Per assegnare nuovi amministratori (amministratori):
1. Accedere a https://manage.visualstudio.com usando un indirizzo di posta elettronica assegnato come amministratore con privilegi avanzati nel contratto tramite cui sono state acquistate le sottoscrizioni.
2. Fare clic sulla scheda **Manage Administrators** (Gestisci amministratori).
3. Fare clic su **Aggiungi**.
   > [!div class="mx-imgBorder"]
   > ![Add admins](_img/admin-roles/add-admins.png "Fare clic sul pannello Gestisci amministratori e quindi su Aggiungi per assegnare nuovi amministratori.")
4. Completare il modulo con le informazioni del nuovo amministratore.  
   > [!div class="mx-imgBorder"]
   > ![Modulo Aggiungi amministratore](_img/admin-roles/add-form.png "Immettere le informazioni di accesso per il nuovo amministratore e scegliere se renderlo un amministratore con privilegi super.  Fare quindi clic su Aggiungi.")

   > [!NOTE]
   > Se si vuole che questo amministratore sia in grado di assegnare altri amministratori, ricordarsi di selezionare la casella **Super Admin** (Amministratore con privilegi avanzati).

5. Dopo aver fatto clic su **Add** (Aggiungi) per assegnare il nuovo amministratore, questi riceverà un messaggio di posta elettronica con l'invito ad accedere al portale.  

## <a name="resources"></a>Risorse
- [Visual Studio di amministrazione e sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Vedere come [assegnare le sottoscrizioni](assign-license.md)
- Vedere altre informazioni su tutti i [vantaggi della sottoscrizione](https://visualstudio.microsoft.com/vs/benefits/)
- [Impostare le preferenze per i contratti](admin-preferences.md)