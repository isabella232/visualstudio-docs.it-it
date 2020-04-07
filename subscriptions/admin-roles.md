---
title: Ruoli di amministratore con privilegi avanzati e amministratore nel portale di amministrazione
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 04/07/2020
ms.topic: conceptual
description: Informazioni sui ruoli di amministratore con privilegi avanzati e amministratore e su come assegnare gli amministratori.
ms.openlocfilehash: 234153dcb8dd06b33ab7aac78e587439684963f9
ms.sourcegitcommit: 1f7aed335c48215dff5c151f76f22e3f10e8b564
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2020
ms.locfileid: "80808384"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Amministratori con privilegi avanzati e amministratori per i contratti di sottoscrizione di Visual Studio

Esistono due diversi ruoli nel nuovo portale di amministrazione delle sottoscrizioni di Visual Studio per i clienti con contratti multilicenza. Questi ruoli sono, ad esempio, il ruolo di contatto principale/per le comunicazioni e il ruolo di gestione delle sottoscrizioni che esisteva già in VLSC.

**Super amministratori:** Quando un'organizzazione è inizialmente configurata, il contatto principale o avvisi diventa un amministratore con privilegi avanzati per impostazione predefinita. Il contatto principale o per le comunicazioni può scegliere di assegnare altri amministratori con privilegi avanzati o amministratori. Un amministratore con privilegi elevati può aggiungere e rimuovere altri amministratori e sottoscrittori. Se nel sistema sono presenti più di due amministratori con privilegi elevati, è possibile eliminarli tutti tranne gli ultimi due per motivi di sicurezza.

**Amministratori:** Un amministratore può essere assegnato solo da un amministratore con privilegi avanzati. Un amministratore può gestire i sottoscrittori solo negli accordi che l'amministratore con privilegi avanzati assegna loro.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Assegnazione di amministratori
Per assegnare nuovi amministratori:
1. Accedere a https://manage.visualstudio.com usando un indirizzo di posta elettronica assegnato come amministratore con privilegi avanzati nel contratto tramite cui sono state acquistate le sottoscrizioni.
2. Fare clic sulla scheda **Manage Administrators** (Gestisci amministratori).
3. Fare clic su **Aggiungi**.
   > [!div class="mx-imgBorder"]
   > ![Aggiungere amministratori](_img/admin-roles/add-admins.png)
4. Completare il modulo con le informazioni del nuovo amministratore.  
   > [!div class="mx-imgBorder"]
   > ![Modulo per aggiungere un amministratore](_img/admin-roles/add-form.png)

   > [!NOTE]
   > Se si vuole che questo amministratore sia in grado di assegnare altri amministratori, ricordarsi di selezionare la casella **Super Admin** (Amministratore con privilegi avanzati).

5. Dopo aver fatto clic su **Add** (Aggiungi) per assegnare il nuovo amministratore, questi riceverà un messaggio di posta elettronica con l'invito ad accedere al portale.  

## <a name="resources"></a>Risorse
- [Supporto per l'amministrazione e le sottoscrizioni di Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](https://docs.microsoft.com/azure/devops/)
- [Documentazione di Azure](https://docs.microsoft.com/azure/)
- [Documentazione di Microsoft 365](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Passaggi successivi
- Vedere come [assegnare le sottoscrizioni](assign-license.md)
- Vedere altre informazioni su tutti i [vantaggi della sottoscrizione](https://visualstudio.microsoft.com/vs/benefits/)
- [Impostare le preferenze per i contratti](admin-prefs.md) 


