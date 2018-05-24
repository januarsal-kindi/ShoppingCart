<template>
    <div class="row">
            <div class="col-2">
                <p class="has-dynamic-label">
                    <label for="dynamic-label-input">Name </label>
                    <span class="help-text-info">{{info.name}}</span>
                </p>
            </div>
            <div class="col-2">
                <p class="has-dynamic-label">
                    <label for="dynamic-label-input">phone number</label>
                    <span class="help-text-info">{{info.phonenumber}}</span>
                </p>
            </div>
            <div class="col-3">
                <p class="has-dynamic-label">
                    <label for="dynamic-label-input">Email</label>
                    <span class="help-text-info">{{info.email}}</span>
                </p>
            </div>
            <div class="col-2">
                <p class="has-dynamic-label">
                    <label style="font-size:0.7em" for="dynamic-label-input">DropperShipper Name</label>
                    <span class="help-text-info">{{info.nameshipper}}</span>
                </p>
            </div>
            <div class="col-2">
                <p class="has-dynamic-label">
                    <label  style="font-size:0.7em" for="dynamic-label-input">DropperShipper Phone</label>
                    <span class="help-text-info">{{info.phonenumbershipper}}</span>
                </p>
            </div>
        </div>
</template>

<script>
export default {
  props: ['info'],
  name: 'InfoDetail',
 
}
</script>

