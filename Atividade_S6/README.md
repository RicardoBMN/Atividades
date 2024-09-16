# **Esse documento contém:**
1. **Modelo Conceitual**
2. **SQL do Banco de Dados**
3. **XML do Banco de Dados**
4. **Foto do Modelo Lógico**

# **1. Modelo Conceitual**
![image](https://res.cloudinary.com/di57ql5yx/image/upload/v1726526177/modelo_conceitual_sbtct7.png)

# **2. SQL do Banco de Dados**:
-- ---
-- Globals
-- ---

-- SET SQL_MODE="NO_AUTO_VALUE_ON_ZERO";
-- SET FOREIGN_KEY_CHECKS=0;

-- ---
-- Table 'ocdr'
-- 
-- ---

DROP TABLE IF EXISTS `ocdr`;
		
CREATE TABLE `ocdr` (
  `card_code` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `card_name` VARCHAR NULL DEFAULT NULL,
  `card_foreign_name` VARCHAR NULL DEFAULT NULL,
  `card_type` VARCHAR NULL DEFAULT NULL,
  `group_code` VARCHAR NULL DEFAULT NULL,
  `phone_1` VARCHAR NULL DEFAULT NULL,
  `phone_2` VARCHAR NULL DEFAULT NULL,
  `cellular` VARCHAR NULL DEFAULT NULL,
  `note` VARCHAR NULL DEFAULT NULL,
  `card_code_ocdr` INTEGER NULL DEFAULT NULL,
  PRIMARY KEY (`card_code`),
KEY (`card_code`)
);

-- ---
-- Table 'cdr1'
-- 
-- ---

DROP TABLE IF EXISTS `cdr1`;
		
CREATE TABLE `cdr1` (
  `id` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `card_code` INTEGER NULL DEFAULT NULL,
  `adress_type` VARCHAR NULL DEFAULT NULL,
  `adress_name` VARCHAR NULL DEFAULT NULL,
  `type_adress` VARCHAR NULL DEFAULT NULL,
  `street` VARCHAR NULL DEFAULT NULL,
  `street_no` VARCHAR NULL DEFAULT NULL,
  `block` VARCHAR NULL DEFAULT NULL,
  `city` VARCHAR NULL DEFAULT NULL,
  `county` VARCHAR NULL DEFAULT NULL,
  `state` VARCHAR NULL DEFAULT NULL,
  `zip_code` VARCHAR NULL DEFAULT NULL,
  `country` VARCHAR NULL DEFAULT NULL,
  `building_floor_room` VARCHAR NULL DEFAULT NULL,
  `add_type` VARCHAR NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
);

-- ---
-- Table 'cdr7'
-- 
-- ---

DROP TABLE IF EXISTS `cdr7`;
		
CREATE TABLE `cdr7` (
  `id` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `card_code` INTEGER NULL DEFAULT NULL,
  `adress` VARCHAR NULL DEFAULT NULL,
  `tax_id_0` VARCHAR NULL DEFAULT NULL,
  `tax_id_1` VARCHAR NULL DEFAULT NULL,
  `tax_id_2` VARCHAR NULL DEFAULT NULL,
  `tax_id_3` VARCHAR NULL DEFAULT NULL,
  `tax_id_4` VARCHAR NULL DEFAULT NULL,
  `tax_id_5` VARCHAR NULL DEFAULT NULL,
  `tax_id_6` VARCHAR NULL DEFAULT NULL,
  `tax_id_7` VARCHAR NULL DEFAULT NULL,
  `tax_id_8` VARCHAR NULL DEFAULT NULL,
  `line_num` VARCHAR NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
);

-- ---
-- Table 'ocrb'
-- 
-- ---

DROP TABLE IF EXISTS `ocrb`;
		
CREATE TABLE `ocrb` (
  `id` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `card_code` INTEGER NULL DEFAULT NULL,
  `county` VARCHAR NULL DEFAULT NULL,
  `bank_code` VARCHAR NULL DEFAULT NULL,
  `user_no_1` VARCHAR NULL DEFAULT NULL,
  `account_no` VARCHAR NULL DEFAULT NULL,
  `user_no_2` VARCHAR NULL DEFAULT NULL,
  `account_name` VARCHAR NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
);

-- ---
-- Foreign Keys 
-- ---

ALTER TABLE `cdr1` ADD FOREIGN KEY (card_code) REFERENCES `ocdr` (`card_code`);
ALTER TABLE `cdr7` ADD FOREIGN KEY (card_code) REFERENCES `ocdr` (`card_code`);
ALTER TABLE `ocrb` ADD FOREIGN KEY (card_code) REFERENCES `ocdr` (`card_code`);

-- ---
-- Table Properties
-- ---

-- ALTER TABLE `ocdr` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `cdr1` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `cdr7` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `ocrb` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

-- ---
-- Test Data
-- ---

-- INSERT INTO `ocdr` (`card_code`,`card_name`,`card_foreign_name`,`card_type`,`group_code`,`phone_1`,`phone_2`,`cellular`,`note`,`card_code_ocdr`) VALUES
-- ('','','','','','','','','','');
-- INSERT INTO `cdr1` (`id`,`card_code`,`adress_type`,`adress_name`,`type_adress`,`street`,`street_no`,`block`,`city`,`county`,`state`,`zip_code`,`country`,`building_floor_room`,`add_type`) VALUES
-- ('','','','','','','','','','','','','','','');
-- INSERT INTO `cdr7` (`id`,`card_code`,`adress`,`tax_id_0`,`tax_id_1`,`tax_id_2`,`tax_id_3`,`tax_id_4`,`tax_id_5`,`tax_id_6`,`tax_id_7`,`tax_id_8`,`line_num`) VALUES
-- ('','','','','','','','','','','','','');
-- INSERT INTO `ocrb` (`id`,`card_code`,`county`,`bank_code`,`user_no_1`,`account_no`,`user_no_2`,`account_name`) VALUES
-- ('','','','','','','','');

# **3. XML do Banco de Dados**: 

<?xml version="1.0" encoding="utf-8" ?>
<!-- SQL XML created by WWW SQL Designer, https://github.com/ondras/wwwsqldesigner/ -->
<!-- Active URL: https://sql.toad.cz/ -->
<sql>
<datatypes db="mysql">
	<group label="Numeric" color="rgb(238,238,170)">
		<type label="Integer" length="0" sql="INTEGER" quote=""/>
	 	<type label="TINYINT" length="0" sql="TINYINT" quote=""/>
	 	<type label="SMALLINT" length="0" sql="SMALLINT" quote=""/>
	 	<type label="MEDIUMINT" length="0" sql="MEDIUMINT" quote=""/>
	 	<type label="INT" length="0" sql="INT" quote=""/>
		<type label="BIGINT" length="0" sql="BIGINT" quote=""/>
		<type label="Decimal" length="1" sql="DECIMAL" re="DEC" quote=""/>
		<type label="Single precision" length="0" sql="FLOAT" quote=""/>
		<type label="Double precision" length="0" sql="DOUBLE" re="DOUBLE" quote=""/>
	</group>

	<group label="Character" color="rgb(255,200,200)">
		<type label="Char" length="1" sql="CHAR" quote="'"/>
		<type label="Varchar" length="1" sql="VARCHAR" quote="'"/>
		<type label="Text" length="0" sql="MEDIUMTEXT" re="TEXT" quote="'"/>
		<type label="Binary" length="1" sql="BINARY" quote="'"/>
		<type label="Varbinary" length="1" sql="VARBINARY" quote="'"/>
		<type label="BLOB" length="0" sql="BLOB" re="BLOB" quote="'"/>
	</group>

	<group label="Date &amp; Time" color="rgb(200,255,200)">
		<type label="Date" length="0" sql="DATE" quote="'"/>
		<type label="Time" length="0" sql="TIME" quote="'"/>
		<type label="Datetime" length="0" sql="DATETIME" quote="'"/>
		<type label="Year" length="0" sql="YEAR" quote=""/>
		<type label="Timestamp" length="0" sql="TIMESTAMP" quote="'"/>
	</group>
	
	<group label="Miscellaneous" color="rgb(200,200,255)">
		<type label="ENUM" length="1" sql="ENUM" quote=""/>
		<type label="SET" length="1" sql="SET" quote=""/>
		<type label="Bit" length="0" sql="bit" quote=""/>
	</group>
</datatypes><table x="978" y="69" name="ocdr">
<row name="card_code" null="1" autoincrement="1">
<datatype>INTEGER</datatype>
<default>NULL</default></row>
<row name="card_name" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="card_foreign_name" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="card_type" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="group_code" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="phone_1" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="phone_2" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="cellular" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="note" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="card_code_ocdr" null="1" autoincrement="0">
<datatype>INTEGER</datatype>
<default>NULL</default></row>
<key type="PRIMARY" name="">
<part>card_code</part>
</key>
<key type="INDEX" name="">
<part>card_code</part>
</key>
</table>
<table x="681" y="296" name="cdr1">
<row name="id" null="1" autoincrement="1">
<datatype>INTEGER</datatype>
<default>NULL</default></row>
<row name="card_code" null="1" autoincrement="0">
<datatype>INTEGER</datatype>
<default>NULL</default><relation table="ocdr" row="card_code" />
</row>
<row name="adress_type" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="adress_name" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="type_adress" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="street" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="street_no" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="block" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="city" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="county" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="state" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="zip_code" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="country" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="building_floor_room" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="add_type" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<key type="PRIMARY" name="">
<part>id</part>
</key>
</table>
<table x="991" y="378" name="cdr7">
<row name="id" null="1" autoincrement="1">
<datatype>INTEGER</datatype>
<default>NULL</default></row>
<row name="card_code" null="1" autoincrement="0">
<datatype>INTEGER</datatype>
<default>NULL</default><relation table="ocdr" row="card_code" />
</row>
<row name="adress" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_0" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_1" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_2" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_3" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_4" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_5" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_6" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_7" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="tax_id_8" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="line_num" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<key type="PRIMARY" name="">
<part>id</part>
</key>
</table>
<table x="1259" y="358" name="ocrb">
<row name="id" null="1" autoincrement="1">
<datatype>INTEGER</datatype>
<default>NULL</default></row>
<row name="card_code" null="1" autoincrement="0">
<datatype>INTEGER</datatype>
<default>NULL</default><relation table="ocdr" row="card_code" />
</row>
<row name="county" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="bank_code" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="user_no_1" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="account_no" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="user_no_2" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<row name="account_name" null="1" autoincrement="0">
<datatype>VARCHAR</datatype>
<default>NULL</default></row>
<key type="PRIMARY" name="">
<part>id</part>
</key>
</table>
</sql>

# **4. Imagem Modelo Conceitual**

![image](https://res.cloudinary.com/di57ql5yx/image/upload/v1726526213/modelologico_kz7w3y.png)
