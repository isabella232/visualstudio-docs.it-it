---
title: Visual Studio di sottoscrizione eliminate da Microsoft | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: f853ed9d-3543-4f5f-a754-92381ee03523
ms.date: 09/30/2021
ms.topic: how-to
description: Informazioni sul significato quando viene visualizzata una notifica che indica che Microsoft ha eliminato una sottoscrizione.
ms.openlocfilehash: 8257c93eefe6bd72ec38e98b7978c475bb3e997f
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2021
ms.locfileid: "129366328"
---
# <a name="why-does-my-dashboard-shows-microsoft-removed-a-subscriber"></a>Perché il dashboard mostra che Microsoft ha rimosso un sottoscrittore? 
Nella sezione **Modifiche recenti** del dashboard nel portale [di](https://manage.visualstudio.com)amministrazione è possibile che le sottoscrizioni siano state rimosse e che il motivo sia "Account chiuso".  Questo problema può verificarsi per due motivi.  

## <a name="subscribers-request-closure-of-their-microsoft-accounts"></a>I sottoscrittori richiedono la chiusura degli account Microsoft
Se un sottoscrittore richiede la chiusura di un account Microsoft (MSA) usato per accedere alla sottoscrizione, la sottoscrizione verrà rimossa alla chiusura dell'account del servizio.  

Per altre informazioni, inclusi gli aspetti importanti da considerare prima di chiudere un account, vedere [Come chiudere il account Microsoft](https://support.microsoft.com/account-billing/how-to-close-your-microsoft-account-c1b2d13f-4de6-6e1b-4a31-d9d668849979).

## <a name="subscribers-are-removed-from-azure-active-directory-tenant"></a>I Sottoscrittori vengono rimossi dal tenant Azure Active Directory
Quando un sottoscrittore la cui sottoscrizione è stata assegnata automaticamente usando un gruppo Azure Active Directory (Azure AD) viene rimosso da tale gruppo, la sottoscrizione viene rimossa automaticamente.  

## <a name="what-happens-when-the-account-is-closed"></a>Cosa accade quando l'account viene chiuso?
Se la sottoscrizione viene rimossa, il sottoscrittore perderà immediatamente l'accesso alla sottoscrizione.  Se un sottoscrittore viene rimosso da un Azure AD, le informazioni sulla sottoscrizione verranno rimosse in modo permanente entro 180 giorni.  Se un sottoscrittore chiude l'account del servizio di gestione, le informazioni vengono rimosse immediatamente.  

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://aka.ms/vsadminhelp) per gli amministratori

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
- Se è necessario modificare una sottoscrizione senza eliminarla,  Informazioni su come [modificare le sottoscrizioni](edit-license.md).
- Per trovare una sottoscrizione specifica, vedere [Cercare una sottoscrizione.](search-license.md)
- Per creare un elenco di tutte le sottoscrizioni,  Vedere [Esportare sottoscrizioni](exporting-subscriptions.md).
- Informazioni su come [eliminare sottoscrizioni](delete-license.md). 

