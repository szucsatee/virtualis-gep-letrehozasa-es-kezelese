Virtualis gep letrehozasa es kezelese

Ebben a feladatban virtuális gépeket kell létrehozni és kezelni az Azure CLI segítségével.

Először
Bejelentkezés az Azure-be:

	az login --tenant XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXX

Kérdések:
Melyik előfizetésben vagyok?

	az account list -o table

Ebben milyen erőforráscsoportok vannak?

	az group list --output table

Vannak-e VNet-jeim?

	az network vnet list --output table
	
Ha csak axxx erőforráscsoportban lévőket akarom lekérdezni

	az network vnet list --resource-group "EROFORRASCSOPORT NEVE" --output table    

vNet létrhozás előtte?

	az network vnet create --resource-group "EROFORRASCSOPORT NEVE" --name "VNet neve"

Subnet lekérdezés:

	az network vnet subnet list --resource-group "EROFORRASCSOPORT NEVE" --vnet-name "VNet neve" --output table

Subnet létrehozás:

	az network vnet subnet create --resource-group "EROFORRASCSOPORT NEVE" --vnet-name "VNet neve" --name "SubNet neve" --address-prefixes 10.0.0.0/24       
----kötlező az address-prefixes



Nem húznám az időt VNet-tel és SubNet-tel... ...

**Hozz létre egy új virtuális gépet az Azure CLI segítségével**
Elérhető location-ok listája:

	az account list-locations --output table

Elérhető gép méretek lekérdezése:

	az vm list-sizes --location "pl:westeurope" --output table

Virtuális gép létrehozás:

	az vm create --resource-group "EROFORRASCSOPORT NEVE" --name "VM neve" --size "gép méret neve" --public-ip-sku Standard --admin-username "azureuser" --admin-password "BiztonsagosJelszo123!"


Resource group összes elérhető vm-je

	az vm list --subscription "elofizetesem neve" --resource-group "resource group neve" --output table

VM adatainak lekérdezése

	az vm show --subscription "elofizetesem neve" --resource-group "resource group neve" --name "VM neve"


**Indítsd el a virtuális gépet**

	az vm list --resource-group "resource group neve" --show-details --output table      
vagy

	az vm start --resource-group "resource group neve" --name "VM neve"

IP cím lekérdezés

	az vm list-ip-addresses --resource-group "resource group neve" --name "VM neve" --output table
	
	
**Állítsd le a virtuális gépet**

	az vm deallocate --resource-group "resource group neve" --name "VM neve"     
----leállítva (felszabadítva)

	
**Töröld a virtuális gépet**

	az vm delete --resource-group "resource group neve" --name "VM neve" --yes 

A disk, a Vnet benne maradt, legegyszerűbb, ha az egész resource group-ot törlöm:

	az group delete --name "resource group neve" --yes


_Megjegyzés: Hozz létre Windows és Linux virtuális gépeket is az Azure CLI segítségével._
A különbség annyi, hogy egy + kapcsoló:
-- image

Lekérdezni az op rendszereket:

	az vm image list --output table
UrnAlias -ra hivatkozni a választásnál





