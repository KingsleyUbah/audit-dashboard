<template>
  <header class="bg-white">
    <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
        <h1 class="text-3xl font-bold text-gray-900 text-left">
            Dashboard
        </h1>          
    </div>
  </header>
  <main class="bg-gray-100 w-full">
     <div class="max-w-7xl mx-auto py-6 sm:px-6 lg:px-8 bg-gray-100">       
       <div class="px-4 py-6 sm:px-0">                    
         <div                
              class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5 text-gray-700 max-w-7xl mx-auto bg-gray-100"
          >                   
            <div v-for="event of results.data" :key="event.id" class="row-span-2 animate-fade-in-down order-3 bg-white shadow-md p-4 lg:order-1">                
              <!-- Board name change -->
              <div v-if="event.event == 'board_name_changed'">
                  <div class="flex items-center justify-between mb-4">
                    <span>

                    </span>
                    <div class="text-sm bg-green-500 py-2 px-2 rounded text-white font-bold">
                      Board name changed                      
                    </div>                
                  </div>                                    

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Name changed by:</div>
                    <div>{{event.createdBy.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Organization:</div>
                    <div>{{event.context.organization.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Old name:</div>
                    <div>{{event.details.oldValue}}</div>
                  </div>             

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">New Name:</div>
                    <div>{{event.details.value}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Date:</div>
                    <div>{{event.createdAt.substring(0, 10)}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Time:</div>
                    <div>{{event.createdAt.substring(11, 19)}}</div>
                  </div>     

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">IP Address:</div>
                    <div>{{event.context.ip}}</div>
                  </div>
              </div>

              <!-- /End name change -->

                <!-- Board description change -->
                <div v-else-if="event.event == 'board_description_changed'">
                  <div class="flex items-center justify-between mb-4">
                    <span>

                    </span>
                    <div class="text-sm bg-yellow-300 py-2 px-2 rounded text-black font-bold">
                      Board description changed                      
                    </div>                
                  </div>                                    

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Affected Board:</div>
                    <div>{{event.object.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Description changed by:</div>
                    <div>{{event.createdBy.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Organization:</div>
                    <div>{{event.context.organization.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Old description:</div>
                    <div>{{event.details.oldValue}}</div>
                  </div>             

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">New Desc:</div>
                    <div class="text-right">{{event.details.value}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Date:</div>
                    <div>{{event.createdAt.substring(0, 10)}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Time:</div>
                    <div>{{event.createdAt.substring(11, 19)}}</div>
                  </div>     

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">IP Address:</div>
                    <div>{{event.context.ip}}</div>
                  </div>                
                </div>
                <!-- /End desc change -->

                <!-- Board opened -->
                <div v-else-if="event.event == 'board_opened'">
                  <div class="flex items-center justify-between mb-4">
                    <span>

                    </span>
                    <div class="text-sm bg-blue-800 py-2 px-2 rounded text-white font-bold">
                      Board opened                      
                    </div>                
                  </div>                                                      

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Board Opened by:</div>
                    <div>{{event.createdBy.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Organization:</div>
                    <div>{{event.context.organization.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Role:</div>
                    <div>{{event.details.role}}</div>
                  </div>             

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Board Name</div>
                    <div class="text-right">{{event.object.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Date:</div>
                    <div>{{event.createdAt.substring(0, 10)}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Time:</div>
                    <div>{{event.createdAt.substring(11, 19)}}</div>
                  </div>     

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">IP Address:</div>
                    <div>{{event.context.ip}}</div>
                  </div>
                </div>    
                <!-- /End board opened -->

                <!-- Board sharing -->
                <div v-else-if="event.event == 'board_account_sharing_enabled'">
                  <div class="flex items-center justify-between mb-4">
                    <span>

                    </span>
                    <div class="text-sm bg-red-600 py-2 px-2 rounded text-white font-bold">
                      Enabled Account Sharing
                    </div>                
                  </div>                                                      

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Affected Board:</div>
                    <div>{{event.object.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Enabled by:</div>
                    <div>{{event.createdBy.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Organization:</div>
                    <div>{{event.context.organization.name}}</div>
                  </div>                                  

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Date:</div>
                    <div>{{event.createdAt.substring(0, 10)}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Time:</div>
                    <div>{{event.createdAt.substring(11, 19)}}</div>
                  </div>     

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">IP Address:</div>
                    <div>{{event.context.ip}}</div>
                  </div>
                </div>    
                <!-- /End board sharing -->

                <!-- Board created -->
                <div v-else-if="event.event == 'board_created'">
                  <div class="flex items-center justify-between mb-4">
                    <span>

                    </span>
                    <div class="text-sm bg-pink-600 py-2 px-2 rounded text-white font-bold">
                      New Board Created
                    </div>                
                  </div>                                                      
                  
                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Created by:</div>
                    <div>{{event.createdBy.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Board Name:</div>
                    <div>{{event.object.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Organization:</div>
                    <div>{{event.context.organization.name}}</div>
                  </div>                                  

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Date:</div>
                    <div>{{event.createdAt.substring(0, 10)}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Time:</div>
                    <div>{{event.createdAt.substring(11, 19)}}</div>
                  </div>     

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">IP Address:</div>
                    <div>{{event.context.ip}}</div>
                  </div>
                </div>    
                <!-- /End board created -->

                <!-- Board cover changed -->
                <div v-else>
                  <div class="flex items-center justify-between mb-4">
                    <span>

                    </span>
                    <div class="text-sm bg-purple-700 py-2 px-2 rounded text-white font-bold">
                      Board Cover Changed
                    </div>                
                  </div>                                                      
                  
                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Cover changed by:</div>
                    <div>{{event.createdBy.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-2">
                    <div class="mb-1">Affected Board:</div>
                    <div>{{event.object.name}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Organization:</div>
                    <div>{{event.context.organization.name}}</div>
                  </div>                                  

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Date:</div>
                    <div>{{event.createdAt.substring(0, 10)}}</div>
                  </div>

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">Time:</div>
                    <div>{{event.createdAt.substring(11, 19)}}</div>
                  </div>     

                  <div class="flex justify-between text-sm mb-3">
                    <div class="mb-1">IP Address:</div>
                    <div>{{event.context.ip}}</div>
                  </div>
                </div>    
                <!-- /End board created -->         
            </div>
         </div>
       </div>
    </div>
  </main>
</template>

<style>
</style>
