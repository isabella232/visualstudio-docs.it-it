---
title: Gestione dei ruoli nei servizi cloud di Azure con Visual Studio | Microsoft Docs
description: Informazioni su come aggiungere e rimuovere i ruoli nei servizi cloud di Azure con Visual Studio.
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002890"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Gestione dei ruoli nei servizi cloud di Azure con Visual Studio
Dopo aver creato il servizio cloud di Azure, è possibile aggiungervi nuovi ruoli o rimuovere quelli esistenti. È anche possibile importare un progetto esistente e convertirlo in un ruolo. Ad esempio, è possibile importare un'applicazione web ASP.NET e specificarla come ruolo web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Aggiunta di un ruolo a un servizio cloud di Azure
Nella procedura seguente consente di aggiungere un ruolo web o di lavoro a un progetto di servizio cloud di Azure in Visual Studio.

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, espandere il nodo del progetto

1. Fare doppio clic il **ruoli** nodo per visualizzare il menu di scelta rapida. Dal menu di scelta rapida, selezionare **Add**, quindi selezionare un ruolo web esistente o un ruolo di lavoro dalla soluzione corrente o creare un progetto di ruolo web o di lavoro. È anche possibile selezionare un progetto appropriato, ad esempio un progetto di applicazione web ASP.NET e associarlo a un progetto di ruolo.

    ![Opzioni di menu per aggiungere un ruolo a un progetto di servizio cloud di Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Rimuovere un ruolo da un servizio cloud di Azure
Nella procedura seguente consente di rimuovere un ruolo web o di lavoro da un progetto di servizio cloud di Azure in Visual Studio.

1. Creare o aprire un progetto di servizio cloud di Azure in Visual Studio.

1. Nelle **Esplora soluzioni**, espandere il nodo del progetto

1. Espandere la **ruoli** nodo.

1. Pulsante destro del mouse sul nodo si desidera rimuovere e, dal menu di scelta rapida, selezionare **rimuovere**. 

    ![Opzioni di menu per aggiungere un ruolo a un servizio cloud di Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Aggiungere nuovamente un ruolo a un progetto servizio cloud di Azure
Se si rimuove un ruolo dal progetto servizio cloud ma successivamente si decide di aggiungere il ruolo di nuovo al progetto, solo la dichiarazione del ruolo e gli attributi di base, ad esempio le informazioni di diagnostica e gli endpoint, vengono aggiunti. Nessun risorse o riferimenti aggiuntivi vengono aggiunti per il `ServiceDefinition.csdef` file o al `ServiceConfiguration.cscfg` file. Se si vuole aggiungere queste informazioni, è necessario aggiungerlo manualmente nei file.

Ad esempio, è possibile rimuovere un ruolo del servizio web e successivamente si decide di aggiungere di nuovo questo ruolo la soluzione. In questo caso, si verifica un errore. Per evitare questo errore, è necessario aggiungere il `<LocalResources>` elemento mostrato nel codice XML seguente nel `ServiceDefinition.csdef` file. Usare il nome del ruolo del servizio web aggiunto di nuovo il progetto come parte dell'attributo del nome per il **<LocalStorage>** elemento. In questo esempio, è il nome del ruolo del servizio web **WCFServiceWebRole1**.

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>Passaggi successivi
- [Configurare i ruoli per un servizio cloud di Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
