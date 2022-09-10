.. index:: pair: page; FARM_ENUM
.. _doxid-md_thirdparty_farm-ng-core_farm_ng_core_enum__r_e_a_d_m_e:

FARM_ENUM
=========

FARM_ENUM is a small c++ macro library to add compile-time introspection to c++ enum classes. This is a fork of `https://github.com/facebookincubator/MY_ENUM <https://github.com/facebookincubator/MY_ENUM>`__.



.. _doxid-md_thirdparty_farm-ng-core_farm_ng_core_enum__r_e_a_d_m_e_1autotoc_md1:

Examples
~~~~~~~~

For example ``:ref:`FARM_ENUM(FooBar, int, (foo, bar)) <doxid-enum_8h_1a5268dfdcfb4a14db714de4e279928ddf>`;`` defines an enum class

.. ref-code-block:: cpp

	enum class FooBar : int {
	  foo,
	  bar
	};

with the following free functions:

.. ref-code-block:: cpp

	// Returns corresponding string of given value
	//
	// Preconditions: value must be a valid enum value, i.e. FooBar::foo, or
	//                FooBar::bar.
	//
	std::string toString(FooBar value);
	
	// Returns corresponding string view of given value
	//
	// Preconditions: value must be a valid enum value, i.e. FooBar::foo, or
	//                FooBar::bar.
	//
	string_view toStringView(FooBar value);
	
	// Returns pretty string representation of given value
	//
	// Preconditions: value must be a valid enum value, i.e. FooBar::foo, or
	//                FooBar::bar.
	//
	std::string toPretty(FooBar value);
	
	// Sets enum given corresponding string, if string is valid (i.e. "foo" or
	// "bar"). Returns false otherwise.
	//
	bool trySetFromString(FooBar& value, std::string str);
	
	// Return count of enum type. First argument is needed for ADL only.
	//
	constexpr size_t getCount(FooBar) {
	  return 2;
	}
	
	// Return string views of enum type. First argument is needed for ADL only.
	std::array<string_view, 2> getStrings(FooBar) {
	  return {"foo", "bar"};
	}
	
	// Return string of enum names. First argument is needed for ADL only.
	std::array<string_view, 2> getStrings(FooBar) {
	  return "foo, bar";
	}
	
	// Return values of enum type. First argument is needed for ADL only.
	constexpr std::array<int, 2> getValues(FooBar) {
	  return {0, 1};
	}
	
	// Returns the position of enum value in the enum class. This is the inverse
	// of `getValues(FooBar)[i]`.
	constexpr size_t getPosition(FooBar value) {
	  switch(value) {
	    case FooBar::foo: { return 0; }
	    case FooBar::bar: { return 1; }
	  }
	}
	
	// Return string representation of type name. First argument is needed for
	// ADL only.
	string_view getTypeName(FooBar) {
	  return "FooBar";
	}

