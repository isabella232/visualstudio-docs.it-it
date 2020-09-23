---
title: Ruoli di amministratore con privilegi avanzati e amministratore nel portale di amministrazione
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 09/21/2020
ms.topic: conceptual
description: Informazioni sui ruoli di amministratore con privilegi avanzati e amministratore e su come assegnare gli amministratori.
ms.openlocfilehash: fc44845ed403e9bf942761203b75c2277fd1aff2
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022702"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Amministratori con privilegi avanzati e amministratori per i contratti di sottoscrizione di Visual Studio

Esistono due diversi ruoli nel nuovo portale di amministrazione delle sottoscrizioni di Visual Studio per i clienti con contratti multilicenza. Questi ruoli sono, ad esempio, il ruolo di contatto principale/per le comunicazioni e il ruolo di gestione delle sottoscrizioni che esisteva già in VLSC.

**Amministratori con privilegi avanzati:** Quando un'organizzazione viene configurata inizialmente, per impostazione predefinita il contatto principale o per le comunicazioni diventa un amministratore con privilegi avanzati. Il contatto principale o per le comunicazioni può scegliere di assegnare altri amministratori con privilegi avanzati o amministratori. Un amministratore con privilegi elevati può aggiungere e rimuovere altri amministratori e sottoscrittori. Se nel sistema sono presenti più di due amministratori con privilegi elevati, è possibile eliminarli tutti tranne gli ultimi due per motivi di sicurezza.

**Amministratori:** Un amministratore può essere assegnato solo da un amministratore con privilegi avanzati. Un amministratore può gestire solo i sottoscrittori nei contratti assegnati dall'amministratore con privilegi avanzati.

Guarda una dimostrazione sulla gestione degli amministratori. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Assegnazione di amministratori
Per assegnare nuovi amministratori:
1. Accedere a https://manage.visualstudio.com usando un indirizzo di posta elettronica assegnato come amministratore con privilegi avanzati nel contratto tramite cui sono state acquistate le sottoscrizioni.
2. Fare clic sulla scheda **Manage Administrators** (Gestisci amministratori).
3. Scegliere **Aggiungi**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere amministratori](_img/admin-roles/add-admins.png "Fare clic sul pannello Gestisci amministratori, quindi su Aggiungi per assegnare nuovi amministratori.")
4. Completare il modulo con le informazioni del nuovo amministratore.  
   > [!div class="mx-imgBorder"]
   > ![Modulo per aggiungere un amministratore](_img/admin-roles/add-form.png "Immettere le informazioni di accesso per il nuovo amministratore e scegliere se renderle un amministratore con privilegi avanzati.  Quindi fare clic su Aggiungi.")

   > [!NOTE]
   > Se si vuole che questo amministratore sia in grado di assegnare altri amministratori, ricordarsi di selezionare la casella **Super Admin** (Amministratore con privilegi avanzati).

5. Dopo aver fatto clic su **Add** (Aggiungi) per assegnare il nuovo amministratore, questi riceverà un messaggio di posta elettronica con l'invito ad accedere al portale.  

## <a name="resources"></a>Risorse
- [Supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)


## <a name="next-steps"></a>Passaggi successivi
- Vedere come [assegnare le sottoscrizioni](assign-license.md)
- Vedere altre informazioni su tutti i [vantaggi della sottoscrizione](https://visualstudio.microsoft.com/vs/benefits/)
- [Impostare le preferenze per i contratti](admin-prefs.md)