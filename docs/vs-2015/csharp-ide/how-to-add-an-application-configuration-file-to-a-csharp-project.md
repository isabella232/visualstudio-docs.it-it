---
title: "Procedura: Aggiungere un File di configurazione dell'applicazione per un C# progetto | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c85690b34f0db705fe2a17e2f98d5b4f11433b3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60044976"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: Aggiungere un File di configurazione dell'applicazione per un C# progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aggiungendo un file di configurazione dell'applicazione (file app.config) a un progetto C#, è possibile personalizzare il modo in cui CLR individua e carica i file di assembly. Per altre informazioni sui file di configurazione dell'applicazione, vedere [modo in cui il Runtime individua gli assembly](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  Non supporta il Windows Store <xref:System.Configuration>. Di conseguenza, le app di Store non contengono un modello di App. config.  
  
 Quando si compila il progetto, l'ambiente di sviluppo copia automaticamente il file app. config, modifica il nome di file della copia in modo che corrisponda il file eseguibile e quindi sposta la copia nella directory bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Per aggiungere un file di configurazione dell'applicazione al progetto c#  
  
1. Nella barra dei menu, scegliere **Project**, **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2. Espandere **Installed**, espandere **elementi di Visual c#** e quindi scegliere il **File di configurazione dell'applicazione** modello.  
  
3. Nella casella di testo **Nome** immettere un nome e quindi scegliere il pulsante **Aggiungi**.  
  
     Un file denominato app. config viene aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle impostazioni di un'applicazione (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schema dei file di configurazione](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Configurazione di app](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Procedura: Configurare un'App per una versione di .NET Framework di destinazione](http://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual Studio Development Environment for C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) (Uso dell'ambiente di sviluppo di Visual Studio per C#)