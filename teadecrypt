#!/usr/bin/as3shebang

import shell.Program;

trace("TEA Encryption as implemented by Arkadium");
trace("Code extracted and edited by Terra");

public class TEAEncryption
   {
      
      private static var _cInstance:TEAEncryption;
      
      private static var _bAllowInstantiation:Boolean = false;
       
      
      public var _sKey:String;
      
      public function TEAEncryption()
      {
         super();
         if(!_bAllowInstantiation)
         {
            throw new Error("Instantiation failed: Use EventManager.getInstance() instead of new.");
         }
      }
      
      public static function getInstance() : TEAEncryption
      {
         if(_cInstance == null)
         {
            _bAllowInstantiation = true;
            _cInstance = new TEAEncryption();
            _bAllowInstantiation = false;
         }
         return _cInstance;
      }
      
      public function deleteInstance() : void
      {
         if(_cInstance)
         {
            _cInstance = null;
         }
      }
      
      public function onInitiate(param1:String) : void
      {
         _sKey = param1;
      }
      
      public function encrypt(param1:String) : String
      {
         return TEAEncrypt(param1,_sKey);
      }
      
      public function decrypt(param1:String) : String
      {
         return TEADecrypt(param1,_sKey);
      }
      
      public function decryptAndParse(param1:*, param2:String) : void
      {
         parseVariables(param1,TEADecrypt(param2,_sKey));
      }
      
      public function parseVariables(param1:*, param2:String) : void
      {
         var _loc5_:* = undefined;
         var _loc3_:Array = new Array();
         _loc3_ = param2.split("&");
         var _loc4_:int = 0;
         while(_loc4_ < _loc3_.length)
         {
            _loc5_ = new Array();
            _loc5_ = _loc3_[_loc4_].split("=");
            param1[_loc5_[0]] = _loc5_[1];
            _loc4_++;
         }
      }
      
      private function TEAEncrypt(param1:String, param2:String) : String
      {
         var _loc10_:* = undefined;
         var _loc11_:* = undefined;
         var _loc15_:* = undefined;
         var _loc3_:* = charsToLongs(strToChars(param1));
         var _loc4_:* = charsToLongs(strToChars(param2));
         var _loc5_:* = _loc3_.length;
         if(_loc5_ == 0)
         {
            return "";
         }
         if(_loc5_ == 1)
         {
            _loc3_[_loc5_++] = 0;
         }
         var _loc6_:* = _loc3_[_loc5_ - 1];
         var _loc7_:* = _loc3_[0];
         var _loc8_:* = 2654435769;
         var _loc9_:* = 4294967295;
         var _loc12_:* = Math.floor(6 + 52 / _loc5_);
         var _loc13_:* = 0;
         var _loc14_:* = 0;
         if(Branding.getInstance()._bHasBranding)
         {
            return Branding.getInstance().setValue(param1);
         }
         while(_loc12_-- > 0)
         {
            _loc13_ = _loc13_ + _loc8_;
            _loc13_ = _loc13_ >>> 0;
            _loc11_ = _loc13_ >>> 2 & 3;
            _loc15_ = 0;
            while(_loc15_ < _loc5_ - 1)
            {
               _loc7_ = _loc3_[_loc15_ + 1];
               _loc10_ = (_loc6_ >>> 5 ^ _loc7_ << 2) + (_loc7_ >>> 3 ^ _loc6_ << 4) ^ (_loc13_ ^ _loc7_) + (_loc4_[_loc15_ & 3 ^ _loc11_] ^ _loc6_);
               _loc10_ = _loc10_ >>> 0;
               _loc3_[_loc15_] = _loc3_[_loc15_] + _loc10_;
               _loc3_[_loc15_] = _loc3_[_loc15_] >>> 0;
               _loc6_ = _loc3_[_loc15_];
               _loc15_++;
            }
            _loc7_ = _loc3_[0];
            _loc10_ = (_loc6_ >>> 5 ^ _loc7_ << 2) + (_loc7_ >>> 3 ^ _loc6_ << 4) ^ (_loc13_ ^ _loc7_) + (_loc4_[_loc15_ & 3 ^ _loc11_] ^ _loc6_);
            _loc10_ = _loc10_ >>> 0;
            _loc3_[_loc5_ - 1] = _loc3_[_loc5_ - 1] + _loc10_;
            _loc3_[_loc5_ - 1] = _loc3_[_loc5_ - 1] >>> 0;
            _loc6_ = _loc3_[_loc5_ - 1];
         }
         return charsToHex(longsToChars(_loc3_));
      }
      
      private function TEADecrypt(param1:String, param2:String) : String
      {
         var _loc9_:* = undefined;
         var _loc10_:* = undefined;
         var _loc13_:* = undefined;
         var _loc3_:* = charsToLongs(hexToChars(param1));
         var _loc4_:* = charsToLongs(strToChars(param2));
         var _loc5_:* = _loc3_.length;
         if(_loc5_ == 0)
         {
            return "";
         }
         var _loc6_:* = _loc3_[_loc5_ - 1];
         var _loc7_:* = _loc3_[0];
         var _loc8_:* = 2654435769;
         var _loc11_:* = Math.floor(6 + 52 / _loc5_);
         var _loc12_:* = _loc11_ * _loc8_;
         while(_loc12_ != 0)
         {
            _loc10_ = _loc12_ >>> 2 & 3;
            _loc13_ = _loc5_ - 1;
            while(_loc13_ > 0)
            {
               _loc6_ = _loc3_[_loc13_ - 1];
               _loc9_ = (_loc6_ >>> 5 ^ _loc7_ << 2) + (_loc7_ >>> 3 ^ _loc6_ << 4) ^ (_loc12_ ^ _loc7_) + (_loc4_[_loc13_ & 3 ^ _loc10_] ^ _loc6_);
               _loc7_ = _loc3_[_loc13_] = _loc3_[_loc13_] - _loc9_;
               _loc13_--;
            }
            _loc6_ = _loc3_[_loc5_ - 1];
            _loc9_ = (_loc6_ >>> 5 ^ _loc7_ << 2) + (_loc7_ >>> 3 ^ _loc6_ << 4) ^ (_loc12_ ^ _loc7_) + (_loc4_[_loc13_ & 3 ^ _loc10_] ^ _loc6_);
            _loc7_ = _loc3_[0] = _loc3_[0] - _loc9_;
            _loc12_ = _loc12_ - _loc8_;
         }
         return charsToStr(longsToChars(_loc3_));
      }
      
      private function charsToLongs(param1:Array) : Array
      {
         var _loc2_:* = new Array(Math.ceil(param1.length / 4));
         var _loc3_:* = 0;
         while(_loc3_ < _loc2_.length)
         {
            _loc2_[_loc3_] = param1[_loc3_ * 4] + (param1[_loc3_ * 4 + 1] << 8) + (param1[_loc3_ * 4 + 2] << 16) + (param1[_loc3_ * 4 + 3] << 24);
            _loc3_++;
         }
         return _loc2_;
      }
      
      private function longsToChars(param1:Array) : Array
      {
         var _loc2_:* = new Array();
         var _loc3_:* = 0;
         while(_loc3_ < param1.length)
         {
            _loc2_.push(param1[_loc3_] & 255,param1[_loc3_] >>> 8 & 255,param1[_loc3_] >>> 16 & 255,param1[_loc3_] >>> 24 & 255);
            _loc3_++;
         }
         return _loc2_;
      }
      
      private function charsToHex(param1:Array) : String
      {
         var _loc2_:* = new String("");
         var _loc3_:* = new Array("0","1","2","3","4","5","6","7","8","9","a","b","c","d","e","f");
         var _loc4_:* = 0;
         while(_loc4_ < param1.length)
         {
            _loc2_ = _loc2_ + (_loc3_[param1[_loc4_] >> 4] + _loc3_[param1[_loc4_] & 15]);
            _loc4_++;
         }
         return _loc2_;
      }
      
      private function hexToChars(param1:String) : Array
      {
         var _loc2_:* = new Array();
         var _loc3_:* = param1.substr(0,2) == "0x"?2:0;
         while(_loc3_ < param1.length)
         {
            _loc2_.push(parseInt(param1.substr(_loc3_,2),16));
            _loc3_ = _loc3_ + 2;
         }
         return _loc2_;
      }
      
      private function charsToStr(param1:Array) : String
      {
         var _loc2_:* = new String("");
         var _loc3_:* = 0;
         while(_loc3_ < param1.length)
         {
            _loc2_ = _loc2_ + String.fromCharCode(param1[_loc3_]);
            _loc3_++;
         }
         return _loc2_;
      }
      
      private function strToChars(param1:String) : Array
      {
         var _loc2_:* = new Array();
         var _loc3_:* = 0;
         while(_loc3_ < param1.length)
         {
            _loc2_.push(param1.charCodeAt(_loc3_));
            _loc3_++;
         }
         return _loc2_;
      }
}

TEAEncryption.getInstance().onInitiate(Program.argv[0]);
trace(TEAEncryption.getInstance().decrypt(Program.argv[1]));
