function lib() {
        var _windowContainer = null,
        _guid = null,
        _poll = this,
        _name = '',
        _store = null;

        var header, panel;

        var save = function(){ //Функция сохранения изменений в анкете
            if (!panel.container['form'].pharmId) return false;

            var modifyData = '';

            $.each(_store.getModifiedRecords(), function(index, rec){
                $.each(rec.modified, function(name){
                    modifyData += '&values['+index+']['+name+']=' + rec.data[name];
                });
                modifyData += '&id['+index+']=' + rec.id;
            });
            if (modifyData == '') return;
                $.getJSON('./modules/units/units.php?action=SET_FORMDATA&pharmId='+panel.container['form'].pharmId+'&projectId='+_param.projectId+'&stageId='+_param.stageId + modifyData +'&rnd='+Math.random(), function(data){
                if (!data || !data.result){
                    alert('ошибка сохранения, попробуйте еще раз');
                    //_store.rejectChanges();
                }else if (data.result == true){
                    _store.commitChanges();
                    panel.container['form'].loadData(panel.container['form'].pharmId);
                }
                $.unblockUI();
            }.bind(this));
        }
