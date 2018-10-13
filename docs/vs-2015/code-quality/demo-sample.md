---
title: Demo di esempio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e1332c335387342d381c1e0030c3c66003c3528b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175851"
---
# <a name="demo-sample"></a>Esempio dimostrativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedure seguenti illustrano come creare l'esempio per la [procedura dettagliata: analisi di codice C/C++ per i difetti](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Le procedure di creano:  
  
-   Oggetto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione denominata CppDemo.  
  
-   Un progetto di libreria statica denominata CodeDefects.  
  
-   Un progetto di libreria statica denominata annotazioni.  
  
 Le procedure forniscono inoltre il codice per i file di intestazione e. cpp per librerie statiche.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Creare la soluzione CppDemo e il progetto CodeDefects  
  
1.  Fare clic sui **File** dal menu **New**, quindi fare clic su **nuovo progetto**.  
  
2.  Nel **tipi di progetto** struttura ad albero di elenco, se Visual C++ non è il linguaggio predefinito in Visual Studio espandere **altri linguaggi**.  
  
3.  Espandere **Visual C++**, quindi fare clic su **generali**.  
  
4.  Nelle **modelli**, fare clic su **progetto vuoto**.  
  
5.  Nel **Name** casella di testo, digitare **CodeDefects**.  
  
6.  Selezionare il **Crea directory per soluzione** casella di controllo.  
  
7.  Nel **Nome soluzione** casella di testo, digitare **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurare il progetto CodeDefects come libreria statica  
  
1.  In Esplora soluzioni fare doppio clic su **CodeDefects** e quindi fare clic su **proprietà**.  
  
2.  Espandere **le proprietà di configurazione** e quindi fare clic su **generali**.  
  
3.  Nel **generali** , selezionare il testo nella colonna accanto a **estensione di destinazione**e quindi digitare **lib**.  
  
4.  Nelle **impostazioni predefinite progetto**, fare clic sulla colonna accanto a **tipo di configurazione**, quindi fare clic su **libreria statica (lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Aggiungere il file di origine e di intestazione al progetto CodeDefects.  
  
1.  In Esplora soluzioni, espandere **CodeDefects**, fare doppio clic su **i file di intestazione**, fare clic su **Add**, quindi fare clic su **nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** della finestra di dialogo fare clic su **codice**, quindi fare clic su **File di intestazione (h)**.  
  
3.  Nel **Name** , digitare **bug. cpp** e quindi fare clic su **Add**.  
  
4.  Copiare il codice seguente e incollarlo nella **bug. cpp** del file nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  In Esplora soluzioni fare doppio clic su **file di origine**, scegliere **New**, quindi fare clic su **nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento** finestra di dialogo, fare clic su **File C++ (. cpp)**  
  
7.  Nel **Name** , digitare **bug. cpp** e quindi fare clic su **Add**.  
  
8.  Copiare il codice seguente e incollarlo nel file Bug.h nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Scegliere il **File** menu e quindi fare clic su **Salva tutto**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Aggiungere il progetto di annotazioni e lo configura come una libreria statica  
  
1.  In Esplora soluzioni fare clic su **CppDemo**, scegliere **Add**, quindi fare clic su **nuovo progetto**.  
  
2.  Nel **Aggiungi nuovo progetto** finestra di dialogo espandere Visual C++, fare clic su **generali**, quindi fare clic su **progetto vuoto**.  
  
3.  Nel **nome** casella di testo, digitare **annotazioni**, quindi fare clic su **Add**.  
  
4.  In Esplora soluzioni fare doppio clic su **annotazioni** e quindi fare clic su **proprietà**.  
  
5.  Espandere **le proprietà di configurazione** e quindi fare clic su **generali**.  
  
6.  Nel **generali** , selezionare il testo nella colonna accanto a **estensione di destinazione**e quindi digitare **lib**.  
  
7.  Nelle **impostazioni predefinite progetto**, fare clic sulla colonna accanto a **tipo di configurazione**, quindi fare clic su **libreria statica (lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Aggiungere il file di intestazione e il file di origine per il progetto di annotazioni  
  
1.  In Esplora soluzioni, espandere **annotazioni**, fare doppio clic su **i file di intestazione**, fare clic su **Add**, quindi fare clic su **nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo, fare clic su **File di intestazione (h)**.  
  
3.  Nel **Name** , digitare **Annotations. h** e quindi fare clic su **Add**.  
  
4.  Copiare il codice seguente e incollarlo nella **Annotations. h** del file nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  In Esplora soluzioni fare doppio clic su **file di origine**, scegliere **New**, quindi fare clic su **nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento** finestra di dialogo, fare clic su **codice** e quindi fare clic su **File C++ (. cpp)**  
  
7.  Nel **Name** , digitare **Annotations. cpp** e quindi fare clic su **Add**.  
  
8.  Copiare il codice seguente e incollarlo nella **Annotations. cpp** del file nei [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Scegliere il **File** menu e quindi fare clic su **Salva tutto**.



