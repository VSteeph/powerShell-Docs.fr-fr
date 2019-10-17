---
title: Paramètres de sécurité | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369498"
---
# <a name="security-parameters"></a>Paramètres de sécurité

Le tableau suivant répertorie les noms et les fonctionnalités recommandés pour les paramètres utilisés pour fournir des informations de sécurité pour une opération, telles que les paramètres qui spécifient la clé de certificat et les informations de privilège.

|Paramètre|Fonctionnalités|
|---|---|
|**ACL**<br>Type de données : chaîne|Implémentez ce paramètre pour spécifier le niveau de contrôle d’accès de protection d’un catalogue ou d’un Uniform Resource Identifier (URI).|
|**CertFile**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom d’un fichier qui contient l’un des éléments suivants :<br>-Un certificat x. 509 encodé en base64 ou Distinguished Encoding Rules (DER)<br>-Un fichier PKCS (Public Key Cryptography Standards) #12 qui contient au moins un certificat et une clé|
|**CertIssuerName**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom de l’émetteur d’un certificat ou pour que l’utilisateur puisse spécifier une sous-chaîne.|
|**CertRequestFile**<br>Type de données : chaîne|Implémentez ce paramètre pour spécifier le nom d’un fichier qui contient une demande de certificat de #10 PKCS encodé en base64 ou DER.|
|**CertSerialNumber**<br>Type de données : chaîne|Implémentez ce paramètre pour spécifier le numéro de série qui a été émis par l’autorité de certification.|
|**CertStoreLocation**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’emplacement du magasin de certificats. L’emplacement correspond généralement à un chemin d’accès de fichier.|
|**CertSubjectName**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’émetteur d’un certificat ou pour que l’utilisateur puisse spécifier une sous-chaîne.|
|**CertUsage**<br>Type de données : chaîne|Implémentez ce paramètre pour spécifier l’utilisation de la clé ou l’utilisation améliorée de la clé. La clé peut être représentée sous la forme d’un masque de bits, d’un bit, d’un identificateur d’objet (OID) ou d’une chaîne.|
|**Justificative**<br>Type de données : [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implémentez ce paramètre afin que l’applet de commande invite automatiquement l’utilisateur à entrer un nom d’utilisateur ou un mot de passe. Une invite s’affiche si les informations d’identification complètes ne sont pas fournies directement.|
|**CSPName**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom du fournisseur de services de certificats (CSP).|
|**CSPType**<br>Type de données : entier|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le type de fournisseur de services de chiffrement.|
|**Groupe**<br>Type de données : chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une collection de principaux pour l’accès. Pour plus d’informations, consultez la description du paramètre **principal** .|
|**Keyalgorithme**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier l’algorithme de génération de clé à utiliser pour la sécurité.|
|**KeyContainerName**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le nom du conteneur de clé.|
|**KeyLength**<br>Type de données : entier|Implémentez ce paramètre afin que l’utilisateur puisse spécifier la longueur de la clé en bits.|
|**Opération**<br>Type de données : chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une action qui peut être effectuée sur un objet protégé.|
|**Directeur**<br>Type de données : chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier une entité identifiable unique pour l’accès.|
|**Limités**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le droit qu’une applet de commande doive exécuter pour une entité particulière.|
|**Privilèges**<br>Type de données : tableau de privilèges|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier les droits nécessaires à l’exécution d’une applet de commande pour une entrée particulière.|
|**Actif**<br>Type de données : chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un ensemble d’opérations qui peuvent être effectuées par une entité.|
|**SaveCred**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les informations d’identification précédemment enregistrées par l’utilisateur soient utilisées lorsque le paramètre est spécifié.|
|**Étendue**<br>Type de données : chaîne|Implémentez ce paramètre afin que l’utilisateur puisse spécifier le groupe d’objets protégés pour l’applet de commande.|
|**SID**<br>Type de données : chaîne|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier un identificateur unique qui représente un principal.|
|**TPM**<br>Type de données : Paramètre_booléen|Implémentez ce paramètre afin que les niveaux de confiance soient pris en charge lorsque le paramètre est spécifié.|
|**TrustLevel**<br>Type de données : mot clé|Implémentez ce paramètre pour permettre à l’utilisateur de spécifier le niveau de confiance pris en charge. Par exemple, les valeurs possibles sont Internet, intranet et FullTrust.|

## <a name="see-also"></a>Voir aussi

[Paramètres d’applet de commande](./cmdlet-parameters.md)

[Écriture d’une applet de commande Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)