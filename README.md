# unwind-rpc 🎉
A standalone call back system , originally created for np based servers can be used in any framework.


# Usage

add ths to your fxmanifest or resources file 
    
    client_scripts '@unwind-rpc/client/cl_main.lua'
    server_scripts '@unwind-rpc/server/sv_main.lua'

Example : Client Side

    local employment = RPC.execute("GetEmploymentInformation", { character = { id = characterId } })


Example : Server Side

    RPC.register("GetEmploymentInformation", function (params)
        local cid = params['character'].id
        exports.ghmattimysql:execute('SELECT * FROM character_passes WHERE cid = @cid', {['cid'] = cid}, function(result)
            if result[1] ~= nil then
                pDataPass = {
                    code = result[1].pass_type,
                    permissions = "property_keys"
                }
            end
        end)

        Citizen.Wait(100)
        return pDataPass
    end)



------------------------------------




## Support
We offer support through [Our Discord Server]([[https://discord.gg/a7XeGhpdpb]())
