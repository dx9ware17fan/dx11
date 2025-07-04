local function isValid(obj)
	return obj and obj ~= 0
end

local function getPosition(obj)
	if not isValid(obj) then return nil end
	local pos = dx9.GetPosition(obj)
	if pos and pos.x and pos.y and pos.z then
		return pos
	end
	return nil
end

local function worldToScreen(pos)
	if not pos then return nil end
	local wts = dx9.WorldToScreen({pos.x, pos.y, pos.z})
	if wts and wts.x and wts.y then
		return wts
	end
	return nil
end

local function detectPlayers()
	local game = dx9.GetDatamodel()
	if not isValid(game) then return end

	local workspace = dx9.FindFirstChild(game, "Workspace")
	if not isValid(workspace) then return end

	local children = dx9.GetChildren(workspace)
	if not children then return end

	for _, child in pairs(children) do
		if isValid(child) then
			local head = dx9.FindFirstChild(child, "Head")

			if isValid(head) then
				local playerName = dx9.GetName(child)
				local headPos = getPosition(head)

				if headPos then
					local face = dx9.FindFirstChildOfClass(head, "Decal")
					local screenPos = worldToScreen(headPos)

					if screenPos then
						if isValid(face) then
							dx9.DrawString({screenPos.x, screenPos.y - 20}, {0, 255, 0}, "[VISIBLE]")
						else
							dx9.DrawString({screenPos.x, screenPos.y - 20}, {255, 0, 0}, "[INVISIBLE]")
						end
					end
				end
			end
		end
	end
end

local function detectPlayersAlternative()
	local game = dx9.GetDatamodel()
	if not isValid(game) then return end

	local players = dx9.FindFirstChild(game, "Players")
	if not isValid(players) then return end

	local playersList = dx9.GetChildren(players)
	if not playersList then return end

	for _, player in pairs(playersList) do
		if isValid(player) then
			local character = dx9.GetCharacter(player)
			if isValid(character) then
				local head = dx9.FindFirstChild(character, "Head")
				if isValid(head) then
					local playerName = dx9.GetName(player)
					local headPos = getPosition(head)

					if headPos then
						local face = dx9.FindFirstChildOfClass(head, "Decal")
						local screenPos = worldToScreen(headPos)

						if screenPos then
							if isValid(face) then
								dx9.DrawString({screenPos.x, screenPos.y - 35}, {0, 255, 0}, "[V]")
							else
								dx9.DrawString({screenPos.x, screenPos.y - 35}, {255, 0, 0}, "[I]")
							end
						end
					end
				end
			end
		end
	end    
end

detectPlayers()
detectPlayersAlternative()

local screenSize = dx9.size()
dx9.DrawString({10, screenSize.height - 30}, {71, 35, 134}, "#Seventeen Family")
