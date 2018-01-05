---
title: 'Procedura: aggiungere un File di configurazione dell''applicazione a un progetto c# | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 707100d33e91d1b0920d008140dc2fb6f1e078fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: aggiungere un file di configurazione dell'applicazione a un progetto C#
Aggiungendo un file di configurazione dell'applicazione (file app. config) a un progetto c#, è possibile personalizzare la modalità di common language runtime individua e carica i file di assembly. Per ulteriori informazioni sui file di configurazione dell'applicazione, vedere [come il Runtime individua gli assembly](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  App UWP non contengono un modello di App. config.
  
 Quando si compila il progetto, l'ambiente di sviluppo consente di copiare automaticamente file app. config, modifica il nome di file della copia in modo che corrisponda il file eseguibile e quindi sposta la copia nella directory bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Per aggiungere un file di configurazione dell'applicazione al progetto c#  
  
1.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Espandere **installato**, espandere **elementi di Visual c#**, quindi scegliere il **File di configurazione applicazione** modello.  
  
3.  Nel **nome** casella di testo, immettere un nome e quindi scegliere il **Aggiungi** pulsante.  
  
     Un file denominato app. config viene aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle impostazioni di un'applicazione (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Schema dei file di configurazione](/dotnet/framework/configure-apps/file-schema/index)   
 [Configurazione di app](/dotnet/framework/configure-apps/index)   
 [Procedura: configurare un'App come destinazione una versione di .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Using the Visual Studio Development Environment for C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) (Uso dell'ambiente di sviluppo di Visual Studio per C#)