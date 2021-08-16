---
title: Gestione dei ruoli nei servizi cloud di Azure
description: Informazioni su come aggiungere e rimuovere i ruoli nei servizi cloud di Azure con Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: d7f89334d4552fa56a046c4a4723bffeeb52d5681f30430f49d783875bbc2357
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363987"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Gestione dei ruoli nei servizi cloud di Azure con Visual Studio
Dopo aver creato il servizio cloud di Azure, è possibile aggiungervi nuovi ruoli o rimuovere quelli esistenti. È possibile anche importare un progetto esistente e convertirlo in un ruolo. Ad esempio, è possibile importare un'applicazione Web ASP.NET e specificarla come ruolo Web.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Aggiungere un ruolo a un servizio cloud di Azure
La procedura seguente consente di aggiungere un ruolo Web o di lavoro a un progetto del servizio cloud di Azure in Visual Studio.

1. Creare o aprire un progetto del servizio cloud di Azure in Visual Studio.

1. In **Esplora soluzioni** espandere il nodo del progetto

1. Fare clic con il pulsante destro del mouse sul nodo **Ruoli** per visualizzare il menu di scelta rapida. Dal menu di scelta rapida selezionare **Aggiungi** quindi selezionare un ruolo Web o di lavoro esistente dalla soluzione corrente o creare un progetto per il ruolo Web o di lavoro. È inoltre possibile selezionare un progetto appropriato, ad esempio un progetto di applicazione Web ASP.NET, e associarlo a un progetto di ruolo.

   ![Opzioni di menu per aggiungere un ruolo a un progetto di servizio cloud di Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Rimuovere un ruolo da un servizio cloud di Azure
La procedura seguente consente di rimuovere un ruolo Web o di lavoro da un progetto del servizio cloud di Azure in Visual Studio.

1. Creare o aprire un progetto del servizio cloud di Azure in Visual Studio.

1. In **Esplora soluzioni** espandere il nodo del progetto

1. Espandere il nodo **Ruoli**.

1. Fare clic con il pulsante destro del mouse sul nodo che si desidera rimuovere e, dal menu di scelta rapida, scegliere **Rimuovi**.

   ![Opzioni di menu per aggiungere un ruolo a un servizio cloud di Azure](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Aggiungere di nuovo un ruolo a un progetto di servizio cloud di Azure
Se si rimuove un ruolo dal progetto di servizio cloud ma in un secondo momento si decide di aggiungere nuovamente tale ruolo al progetto, verranno aggiunti solo la dichiarazione del ruolo e gli attributi di base, ad esempio gli endpoint e le informazioni di diagnostica. Risorse o riferimenti aggiuntivi non vengono aggiunti al file `ServiceDefinition.csdef` o al file `ServiceConfiguration.cscfg`. Se si vuole aggiungere queste informazioni, è necessario aggiungerle di nuovo a questi file in modo manuale.

Ad esempio, è possibile rimuovere un ruolo del servizio Web e poi decidere di aggiungere di nuovo questo ruolo nella soluzione. Se si esegue questa operazione, si verificherà un errore. Per impedire questo errore, è necessario aggiungere nel file `ServiceDefinition.csdef` l'elemento `<LocalResources>` mostrato nel codice XML seguente. Usare il nome del ruolo del servizio Web aggiunto di nuovo nel progetto come parte dell'attributo name per **\<LocalStorage>** l'elemento . In questo esempio il nome del ruolo del servizio Web è **WCFServiceWebRole1**.

```xml
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
```

## <a name="next-steps"></a>Passaggi successivi
- [Configurare i ruoli per un servizio cloud di Azure con Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
